## Тема, Мета, Місце розташування

**Тема:** «СТВОРЕННЯ БАЗИ ДАНИХ У MYSQL. ПІДКЛЮЧЕННЯ NODE.JS ДО MYSQL. РОБОТА З ORM SEQUELIZE.»

**Мета:** 
1. Навчитися створювати базу даних у MySQL.
2. Освоїти виконання SQL-запитів (SELECT, INSERT, UPDATE, DELETE).
3. Підключати серверну програму на Node.js до бази даних.
4. Використовувати ORM Sequelize для роботи з БД.
5. Реалізувати зв’язок One-to-Many між таблицями.

**Місце розташування:**
- GitHub: https://github.com/valeritem/MiniBlog.git
- Live demo: https://mini-blog-client.onrender.com

---

### Завдання

1. **Створити базу даних MongoDB**, яка буде використовуватись власним веб-застосунком (наприклад, `mern-blog`).
2. **Створити колекції** (аналог таблиць у реляційних БД) у базі даних (наприклад, `users`, `posts`, `comments`).
3. **Виконати базові CRUD-запити** (аналог SQL-запитів) на рівні бази даних:
   - `find()` (Читання / аналог SELECT)
   - `insertOne()` / `insertMany()` (Створення / аналог INSERT)
   - `updateOne()` / `updateMany()` (Оновлення / аналог UPDATE)
   - `deleteOne()` / `deleteMany()` (Видалення / аналог DELETE)
4. **Підключити Node.js до MongoDB** за допомогою відповідних пакетів (наприклад, `mongoose`).
5. **Виконати CRUD-запити з Node.js** до бази даних (реалізувати контролери для створення, отримання, редагування та видалення даних).
6. **Використати ODM Mongoose** (Об'єктно-Документне Відображення — NoSQL-аналог ORM) для роботи з даними через JavaScript-об'єкти.
7. **Створити Mongoose-схеми та моделі** для основних сутностей проєкту: `User`, `Post` (та додатково `Comment`).
8. **Реалізувати зв’язок One-to-Many (Один-до-багатьох)**. Наприклад: один користувач має багато статей, а одна стаття містить багато коментарів. Зв'язок реалізувати через збереження масиву ідентифікаторів (`mongoose.Schema.Types.ObjectId`) із властивістю `ref`.

---
## Реалізація таблиці БД
Створення таблиці відбувалось за раніше побудованною ER моделлю.
![ER2](/assets/labs/lab-1/er-diagram2.png)

## Реалізація серверної частини та роботи з БД

### Структура проєкту (Backend)

Проєкт організований за принципом:
* **`config/config.js`** — конфігурація та змінні середовища для підключення до бази даних MongoDB.
```import dotenv from 'dotenv';
import path from 'path';
import { fileURLToPath } from 'url';

const __dirname = path.dirname(fileURLToPath(import.meta.url));

const env = process.env.NODE_ENV || 'development';

dotenv.config({
  path:
    env === 'test' ? path.join(__dirname, '../tests/.env.test') : path.join(__dirname, '../.env'),
});

export default {
  env,
  port: process.env.PORT || 4444,
  mongoUrl: process.env.MONGO_URL,
  jwtSecret: process.env.JWT_SECRET,
};
```

* **`models/`** — опис Mongoose-схем та моделей: 
**`User.js`**
```
import mongoose from 'mongoose';

const UserSchema = new mongoose.Schema(
  {
    username: {
      type: String,
      required: true,
      unigue: true,
    },
    password: {
      type: String,
      required: true,
    },
    posts: [
      {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Post',
      },
    ],
  },
  { timestamps: true }
);

export default mongoose.model('User', UserSchema);
```
**`Post.js`**
```
import mongoose from 'mongoose';

const PostSchema = new mongoose.Schema(
  {
    username: { type: String },
    title: { type: String, required: true },
    text: { type: String, required: true },
    imgUrl: { type: String, default: '' },
    views: { type: Number, default: 0 },
    author: { type: mongoose.Schema.Types.ObjectId, ref: 'User' },
    comments: [{ type: mongoose.Schema.Types.ObjectId, ref: 'Comment' }],
  },
  { timestamps: true }
);
export default mongoose.model('Post', PostSchema);
```
**`Comment.js`**
```
import mongoose from 'mongoose';

const CommentSchema = new mongoose.Schema(
  {
    comment: { type: String, required: true },
    post: { type: mongoose.Schema.Types.ObjectId, ref: 'Post' },
  },
  { timestamps: true }
);

export default mongoose.model('Comment', CommentSchema);
```
    
* **`index.js`** (та `app.js`) — основний файл сервера, налаштування middleware, підключення до бази даних (Mongoose connect) та ініціалізація маршрутів.
![Server db code](/assets/labs/lab-2/server-code.png)
* **`controllers/`** та **`routes/`** — контролери (`auth.js`, `posts.js`, `comments.js`) та маршрути, що інкапсулюють бізнес-логіку. Саме тут реалізовані всі CRUD-операції, які обробляють запити до бази даних.
**`server\controllers\auth.js`**
```
import User from '../models/User.js';
import bcrypt from 'bcryptjs';
import jwt from 'jsonwebtoken';

//  Register user
export const register = async (req, res) => {
  try {
    const { username, password } = req.body;

    const isUsed = await User.findOne({ username });

    if (isUsed) {
      return res.status(409).json({
        message: 'Даний username вже зайнятий. ',
      });
    }

    const salt = bcrypt.genSaltSync(10);
    const hash = bcrypt.hashSync(password, salt);

    const newUser = new User({
      username,
      password: hash,
    });

    await newUser.save();

    const token = jwt.sign(
      {
        id: newUser._id,
      },
      process.env.JWT_SECRET,
      { expiresIn: '30d' }
    );

    res.status(200).json({
      newUser,
      token,
      message: 'Реєстрація пройшла успішно.',
    });
  } catch (error) {
    res.status(500).json({ message: 'Помилка при створені користувача' });
  }
};

// Login user
export const login = async (req, res) => {
  try {
    const { username, password } = req.body;
    const user = await User.findOne({ username });

    if (!user) {
      return res.status(404).json({
        message: 'Такого корситувача не існує.',
      });
    }

    const isPasswordCorrect = await bcrypt.compare(password, user.password);

    if (!isPasswordCorrect) {
      return res.status(400).json({
        message: 'Неправильний пароль.',
      });
    }

    const token = jwt.sign(
      {
        id: user._id,
      },
      process.env.JWT_SECRET,
      { expiresIn: '30d' }
    );

    res.json({
      token,
      user,
      message: 'Ви увійшли в систему.',
    });
  } catch (error) {
    res.status(500).json({ message: 'Помилка при авторизації' });
  }
};
// Get me
export const getMe = async (req, res) => {
  try {
    const user = await User.findById(req.userId);

    if (!user) {
      return res.json({
        message: 'Такого корситувача не існує.',
      });
    }

    const token = jwt.sign(
      {
        id: user._id,
      },
      process.env.JWT_SECRET,
      { expiresIn: '30d' }
    );

    res.json({
      token,
      user,
    });
  } catch (error) {
    res.json({ message: 'Немає доступу.' });
  }
};
```

**`server\controllers\comments.js`**
```
import Comment from '../models/Comment.js';
import Post from '../models/Post.js';

export const createComment = async (req, res) => {
  try {
    //const { postId, comment } = req.body;
    const { comment } = req.body;
    const postId = req.params.id;

    if (!comment) return res.json({ messege: 'Коментар не може бути пустим' });

    const newComment = new Comment({ comment });
    await newComment.save();

    try {
      await Post.findByIdAndUpdate(postId, {
        $push: { comments: newComment._id },
      });
    } catch (error) {
      console.log(error);
    }

    res.status(201).json(newComment);
  } catch (error) {
    res.json({ messege: 'Щось пішло не так.' });
  }
};
```

### Створені колекції моделей `User.js`, `Post.js`, `Comment.js` (виведення через MongoDB Compass або MongoDB Atlas)

1. User model (Модель користувача)
![User collection view](/assets/labs/lab-2/user-collection.png)

2. Post model (Модель статті)
![Post collection view](/assets/labs/lab-2/post-collection.png)

3. Comment model (Модель коментаря)
![Post collection view](/assets/labs/lab-2/comment-collection.png)

---

### Реалізація **Зв'язку One-to-Many**

У MongoDB (за допомогою Mongoose) зв'язки описуються безпосередньо в самих схемах (використовуючи `mongoose.Schema.Types.ObjectId` та `ref`), а не в окремому файлі. 

Зв'язок налаштовано між:
* `User` та `Post` (Один користувач має багато статей). У моделі User масив posts зберігає ідентифікатори всіх статей, створених користувачем. Водночас у моделі Post поле author вказує на конкретного користувача-автора.
```
// ...
    posts: [
      {
        type: mongoose.Schema.Types.ObjectId,
        ref: 'Post', // Посилання на модель Post
      },
    ],
// ...
```
```
// ...
    author: { 
      type: mongoose.Schema.Types.ObjectId, 
      ref: 'User' // Посилання на модель User (автор статті)
    },
// ...
```

* `Post` та `Comment` (Одна стаття має багато коментарів). У моделі Post поле comments є масивом, який зберігає ObjectId всіх залишених під статтею коментарів.
```
// ...
    comments: [
      { 
        type: mongoose.Schema.Types.ObjectId, 
        ref: 'Comment' // Посилання на модель Comment
      }
    ],
// ...
```

* `User` та `Comment` (Один користувач може написати багато коментарів). У моделі Comment вказується посилання на користувача, який залишив цей коментар.
```
// ...
    author: { 
      type: mongoose.Schema.Types.ObjectId, 
      ref: 'User' // Посилання на модель User (автор коментаря)
    },
// ...
```

---

### Програмний код сценаріїв виконання запитів (CRUD)

Замість окремого тестового скрипта, операції створення (Insert), читання (Select), оновлення (Update) та видалення (Delete) інтегровані безпосередньо в API контролери (наприклад, у `controllers/posts.js`). 

Нижче наведено фрагменти коду контролерів, що реалізують демонстрацію операцій згідно з завданням.
```
import { PostService } from 'blog-core';
import { MongoosePostRepository } from '../repositories/MongoosePostRepository.js';
import { LocalFileStorage } from '../services/LocalFileStorage.js';

const postRepository = new MongoosePostRepository();
const fileStorage = new LocalFileStorage();

const postService = new PostService(postRepository, fileStorage);

// Create Post
export const createPost = async (req, res) => {
  try {
    const { title, text } = req.body;

    const createPostDTO = {
      title,
      text,
      authorId: req.userId,
      username: req.body.username,
    };

    if (req.files && req.files.image) {
      createPostDTO.image = {
        name: req.files.image.name,
        data: req.files.image.data,
      };
    }

    const newPost = await postService.createPost(createPostDTO);

    res.status(200).json(newPost);
  } catch (error) {
    console.error(error);
    res.status(500).json({ message: 'Щось пішло не так при створенні поста.' });
  }
};

// Get All Posts
export const getAll = async (req, res) => {
  try {
    const result = await postService.getAllPosts();
    res.json(result);
  } catch (error) {
    console.error(error);
    res.status(500).json({ message: 'Щось пішло не так.' });
  }
};

// Get Post By Id
export const getById = async (req, res) => {
  try {
    const post = await postService.getPostById(req.params.id);
    if (!post) {
      return res.status(404).json({ message: 'Пост не знайдено.' });
    }
    res.json(post);
  } catch (error) {
    res.status(500).json({ message: 'Щось пішло не так.' });
  }
};

// Get My Posts
export const getMyPosts = async (req, res) => {
  try {
    const posts = await postService.getMyPosts(req.userId);
    res.json(posts);
  } catch (error) {
    console.error(error);
    res.status(500).json({ message: 'Щось пішло не так.' });
  }
};

// Remove Post
export const removePost = async (req, res) => {
  try {
    const success = await postService.removePost(req.params.id);

    if (!success) {
      return res.status(404).json({ message: 'Такого поста не існує.' });
    }

    res.json({ message: 'Пост видалено.' });
  } catch (error) {
    res.status(500).json({ message: 'Щось пішло не так.' });
  }
};

// Update Post
export const updatePost = async (req, res) => {
  try {
    const { title, text, id } = req.body;

    const updateDTO = { title, text };

    if (req.files && req.files.image) {
      updateDTO.image = {
        name: req.files.image.name,
        data: req.files.image.data,
      };
    }

    const updatedPost = await postService.updatePost(id, updateDTO);

    if (!updatedPost) {
      return res.status(404).json({ message: 'Пост не знайдено.' });
    }

    res.json(updatedPost);
  } catch (error) {
    res.status(500).json({ message: 'Щось пішло не так.' });
  }
};

// Get Post Comments
import Post from '../models/Post.js';
import Comment from '../models/Comment.js';

export const getPostComments = async (req, res) => {
  try {
    const post = await Post.findById(req.params.id);
    if (!post) {
      return res.status(404).json({ message: 'Пост не знайдено' });
    }

    const list = await Promise.all(
      post.comments.map((comment) => {
        return Comment.findById(comment);
      })
    );
    res.json(list);
  } catch (error) {
    res.json({ message: 'Щось пішло не так.' });
  }
};

```
