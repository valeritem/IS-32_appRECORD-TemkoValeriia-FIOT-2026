## «ВИБІР ПРЕДМЕТНОЇ ОБЛАСТІ. АНАЛІЗ,МОДЕЛЮВАННЯ ТА РОЗРОБЛЕННЯ АДАПТИВНОГО WEB-ЗАСТОСУНКУ

**Тема:** «ВИБІР ПРЕДМЕТНОЇ ОБЛАСТІ. АНАЛІЗ, МОДЕЛЮВАННЯ ТА РОЗРОБЛЕННЯ АДАПТИВНОГО WEB-ЗАСТОСУНКУ»

**Мета:** сформулювати ключові складові опису інформаційної системи:
актуальність, мету та завдання, об’єкт і предмет роботи, практичне
значення, функціональні та нефункціональні вимоги, Use-case та ER-
діаграми.

**Місце розташування:**
- GitHub: https://github.com/valeritem/MiniBlog.git
- Live demo: https://mini-blog-client.onrender.com

---

# Специфікація веб-застосунку MiniBlog

## Актуальність теми
У сучасному цифровому середовищі веб-платформи для публікації контенту набувають все більшої популярності. Блоги та мікроблоги дозволяють користувачам швидко ділитися інформацією, публікувати власні думки, статті та взаємодіяти з іншими користувачами через коментарі.

З розвитком веб-технологій виникає потреба у створенні зручних, швидких та функціональних інформаційних систем, які забезпечують просте створення, редагування та перегляд контенту. Особливо актуальним є використання сучасних технологій веб-розробки, таких як стек MERN (MongoDB, Express.js, React.js, Node.js), який дозволяє створювати масштабовані та ефективні веб-застосунки.

Проблема полягає у необхідності створення системи, яка забезпечує зручну публікацію статей, взаємодію користувачів через коментарі, а також ефективне керування контентом. Тому розробка веб-застосунку MiniBlog є актуальною, оскільки дозволяє реалізувати платформу для створення та перегляду статей із використанням сучасних веб-технологій.

---

## Мета роботи
Метою роботи є розробка веб-застосунку MiniBlog для створення, перегляду та керування статтями користувачів із можливістю коментування, використовуючи стек технологій MERN.

---

## Завдання роботи
Для досягнення поставленої мети необхідно виконати такі завдання:
1. Проаналізувати особливості веб-застосунків для публікації контенту.
2. Розробити архітектуру веб-застосунку на основі стеку MERN.
3. Реалізувати систему реєстрації та авторизації користувачів.
4. Реалізувати функціонал створення, редагування та видалення статей.
5. Реалізувати відображення списку всіх статей на головній сторінці.
6. Реалізувати перегляд повної статті.
7. Реалізувати можливість додавання коментарів до статей.
8. Реалізувати сторінку перегляду власних статей користувача.
9. Реалізувати блок популярних статей.
10. Провести тестування розробленого веб-застосунку.

---

## Об’єкт та предмет роботи

* **Об’єкт роботи:** процес публікації, зберігання та перегляду статей у веб-системах блогового типу.
* **Предмет роботи:** методи та засоби розробки веб-застосунку для створення та керування блоговими статтями з використанням стеку MERN.

---

## Бізнес-логіка роботи системи
Бізнес-логіка веб-застосунку MiniBlog визначає правила створення, редагування, перегляду та коментування статей користувачами, а також обмеження доступу до певних дій. 

**Основні правила роботи системи:**
1. Користувач може створювати статті лише після проходження процедури реєстрації та авторизації.
2. Кожна стаття повинна бути прив’язана до конкретного автора.
3. Користувач має право редагувати або видаляти лише власні статті.
4. Після створення статті вона стає доступною для перегляду іншими користувачами.
5. Користувач може залишати коментарі до статей, якщо він авторизований у системі.
6. Кожен перегляд статті збільшує лічильник її переглядів.
7. Список популярних статей формується на основі кількості переглядів.
8. При видаленні статті вона повинна бути видалена з бази даних разом із пов’язаними коментарями.
9. Дані статей, коментарів та користувачів зберігаються у базі даних та використовуються для подальшого відображення у системі.

> Таким чином, бізнес-логіка системи забезпечує контроль доступу до дій користувачів, обробку інформації про статті та коментарі, а також підтримку взаємодії між користувачами.

---

## Функціональні вимоги
Функціональні вимоги описують функціональність, яку система повинна надавати користувачам.

### Реєстрація та авторизація
* **FR-1.** Система повинна надавати можливість реєстрації нового користувача шляхом введення електронної пошти та пароля.
* **FR-2.** Система повинна перевіряти унікальність електронної пошти під час реєстрації користувача.

### Робота зі статтями
* **FR-4.** Система повинна надавати можливість авторизованому користувачу створювати нову статтю.
* **FR-5.** При створенні статті користувач повинен мати можливість додати:
  * зображення;
  * заголовок;
  * текст статті.
* **FR-6.** Система повинна зберігати створену статтю у базі даних разом з інформацією про автора та дату створення.
* **FR-7.** Система повинна відображати список усіх статей на головній сторінці.
* **FR-8.** Система повинна надавати можливість перегляду повного тексту статті на окремій сторінці.
* **FR-9.** Система повинна збільшувати лічильник переглядів кожного разу, коли користувач відкриває сторінку статті.
* **FR-10.** Система повинна надавати можливість автору редагувати власну статтю.
* **FR-11.** Система повинна надавати можливість автору видаляти власну статтю.

### Робота з коментарями
* **FR-12.** Система повинна надавати можливість авторизованим користувачам залишати коментарі під статтями.
* **FR-13.** Система повинна відображати список коментарів для кожної статті.

### Робота з персональними даними користувача
* **FR-14.** Система повинна надавати користувачу можливість перегляду списку власних статей на сторінці «Мої статті».

### Популярні статті
* **FR-15.** Система повинна формувати список популярних статей на основі кількості переглядів.
* **FR-16.** Система повинна відображати блок популярних статей на головній сторінці.

---

## Нефункціональні вимоги
Нефункціональні вимоги визначають характеристики якості системи та умови її функціонування.

### Вимоги до продуктивності
* **NFR-1.** Система повинна забезпечувати час завантаження сторінки не більше 3 секунд при нормальному навантаженні.
* **NFR-2.** Система повинна підтримувати одночасну роботу не менше 50 користувачів без значного зниження продуктивності.

### Вимоги до безпеки
* **NFR-3.** Система повинна використовувати механізм аутентифікації на основі JWT-токенів.
* **NFR-4.** Система повинна обмежувати доступ до функцій редагування та видалення статей лише для їх авторів.

### Вимоги до зручності використання
* **NFR-5.** Інтерфейс системи повинен бути інтуїтивно зрозумілим для користувача без необхідності додаткового навчання.

### Вимоги до надійності
* **NFR-6.** Система повинна забезпечувати збереження даних у базі даних без їх втрати при звичайній експлуатації.

### Вимоги до сумісності
* **NFR-7.** Система повинна коректно працювати у сучасних браузерах (Google Chrome, Mozilla Firefox, Microsoft Edge).

## Use-case діаграма

![UC](/assets/labs/lab-1/use-case(2).drawio.png)

## ER-діаграма

![ER1](/assets/labs/lab-1/er-diagram1.png)
![ER2](/assets/labs/lab-1/er-diagram2.png)

---

## Стурктура веб-застосунку (client)
### Структура сторінки MainPage.jsx (Головна)
```
import React, { useEffect } from 'react';
import { useDispatch, useSelector } from 'react-redux';
import { getAllPosts } from '../redux/features/post/postSlice';
import { PostItem } from '../components/PostItem';
import { PopularPosts } from '../components/PopularPosts';

export const MainPage = () => {
  const dispatch = useDispatch();
  const { posts, popularPosts } = useSelector((state) => state.post);

  useEffect(() => {
    dispatch(getAllPosts());
  }, [dispatch]);

  if (!posts.length) {
    return (
      <div className="text-xl text-center text-white py-10">
        Постів не існує.
      </div>
    );
  }
  return (
    <div className="max-w-[900px] mx-auto py-10">
      <div className="flex justify-between gap-8">
        <div className="flex flex-col gap-10 basis-4/5">
          {posts?.map((post, idx) => (
            <PostItem key={idx} post={post} />
          ))}
        </div>
        <div className="basis-1/5">
          <div className="text-s uppercase text-white">Популярне:</div>

          {popularPosts?.map((post, idx) => (
            <PopularPosts key={idx} post={post} />
          ))}
        </div>
      </div>
    </div>
  );
};
```

### Структура сторінки LoginPage.jsx (Авторизація)
```
import React, { useState, useEffect } from 'react';
import { Link, useNavigate } from 'react-router-dom';
import { useDispatch, useSelector } from 'react-redux';
import { checkIsAuth, loginUser } from '../redux/features/auth/authSlice';
import { toast } from 'react-toastify';

export const LoginPage = () => {
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');

  const dispatch = useDispatch();
  const navigate = useNavigate();

  const { status, isLoading } = useSelector((state) => state.auth);
  const isAuth = useSelector(checkIsAuth);

  useEffect(() => {
    if (status) toast(status);
    if (isAuth) navigate('/');
  }, [status, isAuth, navigate]);

  const handleSubmit = () => {
    try {
      dispatch(loginUser({ username, password }));

      setUsername('');
      setPassword('');
    } catch (error) {
      console.log(error);
    }
  };

  return (
    <form
      onSubmit={(e) => e.preventDefault()}
      className="w-1/4 h-60 mx-auto mt-40"
    >
      <h1 className="text-lg text-white text-center">Авторизація</h1>

      <label className="text-xs text-gray-400">
        Username:
        <input
          type="text"
          value={username}
          onChange={(e) => setUsername(e.target.value)}
          placeholder="Username"
          className="mt-1 text-black w-full rounded-lg bg-gray-400 border py-1 px-2 text-xs outline-none placeholder:text-gray-700"
        />
      </label>

      <label className="text-xs text-gray-400">
        Password:
        <input
          type="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
          placeholder="Password"
          className="mt-1 text-black w-full rounded-lg bg-gray-400 border py-1 px-2 text-xs outline-none placeholder:text-gray-700"
        />
      </label>

      <div className="flex gap-8 justify-center mt-4">
        <button
          type="submit"
          onClick={handleSubmit}
          disabled={isLoading}
          className="flex justify-center items-center text-xs bg-gray-600 text-white rounded-sm py-2 px-4"
        >
          {isLoading ? 'Зачекайте...' : 'Увійти'}
        </button>

        <Link
          to="/register"
          className="flex justify-center items-center text-xs text-white"
        >
          Немає акаунта?
        </Link>
      </div>
    </form>
  );
};
```
### Структура сторінки RegisterPage.jsx (Реєстрація)
```
import React, { useState, useEffect } from 'react';
import { Link, useNavigate } from 'react-router-dom';
import { useDispatch, useSelector } from 'react-redux';
import { registerUser, checkIsAuth } from '../redux/features/auth/authSlice';
import { toast } from 'react-toastify';

export const RegisterPage = () => {
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');
  const { status } = useSelector((state) => state.auth);
  const isAuth = useSelector(checkIsAuth);

  const dispatch = useDispatch();
  const navigate = useNavigate();

  useEffect(() => {
    if (status) {
      toast(status);
    }
    if (isAuth) navigate('/');
  }, [status, isAuth, navigate]);

  const handleSubmit = () => {
    try {
      dispatch(registerUser({ username, password }));
      setPassword('');
      setUsername('');
    } catch (error) {
      console.log(error);
    }
  };

  return (
    <form
      onSubmit={(e) => e.preventDefault()}
      className="w-1/4 h-60 mx-auto mt-40"
    >
      <h1 className="text-lg text-white text-center">Реєстрація</h1>
      <label className="text-xs text-gray-400">
        Username:
        <input
          type="text"
          value={username}
          onChange={(e) => setUsername(e.target.value)}
          placeholder="Username"
          className="mt-1 text-black w-full rounded-lg bg-gray-400 border py-1 px-2 text-xs outline-none placeholder:text-gray-700"
        />
      </label>

      <label className="text-xs text-gray-400">
        Password:
        <input
          type="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
          placeholder="Password"
          className="mt-1 text-black w-full rounded-lg bg-gray-400 border py-1 px-2 text-xs outline-none placeholder:text-gray-700"
        />
      </label>

      <div className="flex gap-8 justify-center mt-4">
        <button
          type="submit"
          onClick={handleSubmit}
          className="flex justify-center items-center text-xs bg-gray-600 text-white rounded-sm py-2 px-4"
        >
          Підтвердити
        </button>
        <Link
          to="/login"
          className="flex justify-center items-center text-xs text-white"
        >
          Уже зареєстровані ?
        </Link>
      </div>
    </form>
  );
};
```

### Структура сторінки PostsPage.jsx (Список постів)
```
import React, { useState, useEffect } from 'react';
import { PostItem } from '../components/PostItem';
import axios from '../utils/axios';

export const PostsPage = () => {
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    const handlePostUpdated = async () => {
      try {
        const { data } = await axios.get('/posts/user/me');
        setPosts(data);
      } catch (error) {
        console.log(error);
      }
    };

    handlePostUpdated();

    window.addEventListener('postUpdated', handlePostUpdated);

    return () => window.removeEventListener('postUpdated', handlePostUpdated);
  }, []);

  if (!posts.length) {
    return (
      <div className="text-xl text-center text-white py-10">
        Постів не існує.
      </div>
    );
  }

  return (
    <div className="w-1/2 mx-auto py-10 flex flex-col gap-10">
      {posts?.filter(Boolean).map((post, idx) => (
        <PostItem post={post} key={post._id || idx} />
      ))}
    </div>
  );
};

```

### Структура сторінки PostPage.jsx (Сторінка посту)
```
import React, { useCallback, useState, useEffect } from 'react';
import {
  AiFillEye,
  AiOutlineMessage,
  AiTwotoneEdit,
  AiFillDelete,
} from 'react-icons/ai';
import dayjs from 'dayjs';
import { Link, useParams, useNavigate } from 'react-router-dom';
import { useDispatch, useSelector } from 'react-redux';
import { toast } from 'react-toastify';

import axios from '../utils/axios';
import { removePost } from '../redux/features/post/postSlice';
import {
  createComment,
  getPostComments,
} from '../redux/features/comment/commentSlice';
import { CommentItem } from '../components/CommentItem';

export const PostPage = () => {
  const [post, setPost] = useState(null);
  const [comment, setComment] = useState('');

  const { user } = useSelector((state) => state.auth);
  const { comments } = useSelector((state) => state.comment);

  const params = useParams();
  const dispatch = useDispatch();
  const navigate = useNavigate();

  const removePostHandler = () => {
    try {
      dispatch(removePost(params.id));
      toast('Пост видалено');
      navigate('/posts');
    } catch (error) {
      console.log(error);
    }
  };

  const handleSubmit = () => {
    try {
      const postId = params.id;
      dispatch(createComment({ postId, comment }));
      setComment('');
    } catch (error) {
      console.log(error);
    }
  };
  const fetchPost = useCallback(async () => {
    const { data } = await axios.get(`/posts/${params.id}`);
    setPost(data);
  }, [params.id]);

  const fetchComments = useCallback(async () => {
    try {
      dispatch(getPostComments(params.id));
    } catch (error) {
      console.log(error);
    }
  }, [params.id]);

  useEffect(() => {
    fetchPost();
  }, [fetchPost]);

  useEffect(() => {
    fetchComments();
  }, [fetchComments]);

  if (!post) {
    return (
      <div className="text-xl text-center text-white py-10">Загрузка...</div>
    );
  }
  return (
    <div>
      <button className="flex justify-center items-center bg-gray-600 text-xs text-white rounded-sm py-2 px-4">
        <Link className="flex" to={'/'}>
          Назад
        </Link>
      </button>

      <div className="flex gap-10 py-8">
        <div className="w-2/3">
          <div className="flex flex-col basis-1/4 flex-grow">
            <div
              className={
                post?.imgUrl ? 'flex rouded-sm h-80' : 'flex rounded-sm'
              }
            >
              {post?.imgUrl && (
                <img
                  src={`http://localhost:3002/${post.imgUrl}`}
                  alt="img"
                  className="object-cover w-full"
                />
              )}
            </div>
          </div>
          <div className="flex justify-between items-center pt-2">
            <div className="text-xs text-white opacity-50">{post.username}</div>
            <div className="text-xs text-white opacity-50">
              {dayjs(post.createdAt).format('DD.MM.YYYY')}
            </div>
          </div>
          <div className="text-white text-xl">{post.title}</div>
          <p className="text-white opacity-60 text-xs pt-4">{post.text}</p>

          <div className="flex gap-3 items-center mt-2 justify-between">
            <div className="flex gap-3 mt-4">
              <button className="flex items-center justify-center gap-2 text-xs text-white opacity-50">
                <AiFillEye /> <span>{post.views}</span>
              </button>
              <button className="flex items-center justify-center gap-2 text-xs text-white opacity-50">
                <AiOutlineMessage /> <span>{post.comments?.length || 0} </span>
              </button>
            </div>

            {user?._id === post.author && (
              <div className="flex gap-3 mt-4">
                <button className="flex items-center justify-center gap-2 text-white opacity-50">
                  <Link to={`/${params.id}/edit`}>
                    <AiTwotoneEdit />
                  </Link>
                </button>
                <button
                  data-testid="delete-post"
                  onClick={removePostHandler}
                  className="flex items-center justify-center gap-2  text-white opacity-50"
                >
                  <AiFillDelete />
                </button>
              </div>
            )}
          </div>
        </div>
        <div className="w-1/3 p-8 bg-gray-700 flex flex-col gap-2 rounded-sm">
          <form className="flex gap-2" onSubmit={(e) => e.preventDefault()}>
            <input
              type="text"
              value={comment}
              onChange={(e) => setComment(e.target.value)}
              placeholder="Comment"
              className="text-black w-full rounded-sm bg-gray-400 border p-2 text-xs outline-none placeholder:text-gray-700"
            />
            <button
              type="submit"
              onClick={handleSubmit}
              className="flex justify-center items-center bg-gray-600 text-xs text-white rounded-sm py-2 px-4"
            >
              Надіслати
            </button>
          </form>
          {comments?.map((cmt) => (
            <CommentItem key={cmt._id} cmt={cmt} />
          ))}
        </div>
      </div>
    </div>
  );
};
```

### Структура сторінки AddPostPage.jsx (Додати пост)
```import React, { useState } from 'react';
import { useDispatch } from 'react-redux';
import { useNavigate } from 'react-router-dom';
import { createPost } from '../redux/features/post/postSlice';

export const AddPostPage = () => {
  const [title, setTitle] = useState('');
  const [text, setText] = useState('');
  const [image, setImage] = useState('');

  const dispatch = useDispatch();
  const navigate = useNavigate();

  const submitHandler = async () => {
    try {
      const data = new FormData();
      data.append('title', title);
      data.append('text', text);
      data.append('image', image);

      await dispatch(createPost(data));
      navigate('/');
    } catch (error) {
      console.log(error);
    }
  };

  const clearFormHandler = () => {
    setText('');
    setTitle('');
  };

  return (
    <form className="w-1/3 mx-auto py-10" onSubmit={(e) => e.preventDefault()}>
      <label className="text-gray-300 py-2 bg-gray-600 text-xs mt-2 flex items-center justify-center border-2 border-dotted cursor-pointer">
        Прикріпити зображення:
        <input
          type="file"
          className="hidden"
          onChange={(e) => setImage(e.target.files[0])}
        />
      </label>
      <div className="flex object-cover py-2">
        {image && <img src={URL.createObjectURL(image)} alt={image.name} />}
      </div>

      <label className="text-xs text-white opacity-70">
        Заголовок поста:
        <input
          type="text"
          value={title}
          onChange={(e) => setTitle(e.target.value)}
          placeholder="Заголовок"
          className="mt-1 text-black w-full rounded-lg bg-gray-400 border py-1 px-2 text-xs outline-none placeholder:text-gray-700"
        />
      </label>

      <label className="text-xs text-white opacity-70">
        Текст поста:
        <textarea
          onChange={(e) => setText(e.target.value)}
          value={text}
          placeholder="Текст поста"
          className="mt-1 text-black w-full rounded-lg bg-gray-400 border py-1 px-2 text-xs outline-none resize-none h-40 placeholder:text-gray-700"
        />
      </label>

      <div className="flex gap-8 items-center justify-center mt-4">
        <button
          onClick={submitHandler}
          className="flex justify-center items-center bg-gray-600 text-xs text-white rounded-sm py-2 px-4"
        >
          Додати
        </button>

        <button
          onClick={clearFormHandler}
          className="flex justify-center items-center bg-red-500 text-xs text-white rounded-sm py-2 px-4"
        >
          Відмінити
        </button>
      </div>
    </form>
  );
};
```
### Структура сторінки EditPostPage.jsx (Редагувати пост)
```
import React, { useEffect, useState, useCallback } from 'react';
import { useDispatch } from 'react-redux';
import { useNavigate, useParams } from 'react-router-dom';

import axios from '../utils/axios';
import { updatePost } from '../redux/features/post/postSlice';

export const EditPostPage = () => {
  const [title, setTitle] = useState('');
  const [text, setText] = useState('');
  const [oldImage, setOldImage] = useState('');
  const [newImage, setNewImage] = useState('');

  const dispatch = useDispatch();
  const navigate = useNavigate();
  const params = useParams();

  const fetchPost = useCallback(async () => {
    const { data } = await axios.get(`/posts/${params.id}`);
    setTitle(data.title);
    setText(data.text);
    setOldImage(data.imgUrl);
  }, [params.id]);

  const submitHandler = async () => {
    try {
      const updatedPost = new FormData();
      updatedPost.append('title', title);
      updatedPost.append('text', text);
      updatedPost.append('id', params.id);
      updatedPost.append('image', newImage);
      await dispatch(updatePost(updatedPost)).unwrap();
      window.dispatchEvent(new Event('postUpdated'));
      navigate('/posts');
    } catch (error) {
      console.log(error);
    }
  };
  const clearFormHandler = () => {
    setText('');
    setTitle('');
  };

  useEffect(() => {
    fetchPost();
  }, [fetchPost]);

  return (
    <form className="w-1/3 mx-auto py-10" onSubmit={(e) => e.preventDefault()}>
      <label className="text-gray-300 py-2 bg-gray-600 text-xs mt-2 flex items-center justify-center border-2 border-dotted cursor-pointer">
        Прикріпити зображення:
        <input
          type="file"
          className="hidden"
          onChange={(e) => {
            setNewImage(e.target.files[0]);
            setOldImage('');
          }}
        />
      </label>
      <div className="flex object-cover py-2">
        {oldImage && (
          <img src={`http://localhost:3002/${oldImage}`} alt={oldImage.name} />
        )}
        {newImage && (
          <img src={URL.createObjectURL(newImage)} alt={newImage.name} />
        )}
      </div>

      <label className="text-xs text-white opacity-70">
        Заголовок поста:
        <input
          type="text"
          value={title}
          onChange={(e) => setTitle(e.target.value)}
          placeholder="Заголовок"
          className="mt-1 text-black w-full rounded-lg bg-gray-400 border py-1 px-2 text-xs outline-none placeholder:text-gray-700"
        />
      </label>

      <label className="text-xs text-white opacity-70">
        Текст поста:
        <textarea
          onChange={(e) => setText(e.target.value)}
          value={text}
          placeholder="Текст поста"
          className="mt-1 text-black w-full rounded-lg bg-gray-400 border py-1 px-2 text-xs outline-none resize-none h-40 placeholder:text-gray-700"
        />
      </label>

      <div className="flex gap-8 items-center justify-center mt-4">
        <button
          onClick={submitHandler}
          className="flex justify-center items-center bg-gray-600 text-xs text-white rounded-sm py-2 px-4"
        >
          Зберегти
        </button>

        <button
          onClick={clearFormHandler}
          className="flex justify-center items-center bg-red-500 text-xs text-white rounded-sm py-2 px-4"
        >
          Відмінити
        </button>
      </div>
    </form>
  );
};
```

### Структура компоненту CommentItem.jsx 
```
import React from 'react';

export const CommentItem = ({ cmt }) => {
  const avatar = cmt.comment.trim().toUpperCase().slice(0, 2);
  return (
    <div className="flex items-center gap-3">
      <div className="flex items-center justify-center shrink-0 rounded-full w-10 h-10 bg-blue-300 text-sm">
        {avatar}
      </div>
      <div className="flex text-gray-300 text-[10px]">{cmt.comment}</div>
    </div>
  );
};
```

### Структура компоненту Layout.jsx
```
import React from 'react';
import { Navbar } from './Navbar';

export const Layout = ({ children }) => {
  return (
    <React.Fragment>
      <div className="container mx-auto">
        <Navbar />
        {children}
      </div>
    </React.Fragment>
  );
};

```

### Структура компоненту Navbar.jsx
```
import React from 'react';
import { Link, NavLink } from 'react-router-dom';
import { useDispatch, useSelector } from 'react-redux';
import { checkIsAuth, logout } from '../redux/features/auth/authSlice';
import { toast } from 'react-toastify';

export const Navbar = () => {
  const isAuth = useSelector(checkIsAuth);

  const dispatch = useDispatch();

  const activeStyles = {
    color: 'white',
  };

  const logoutHandler = () => {
    dispatch(logout());
    window.localStorage.removeItem('token');
    toast('Ви вийшли з системи');
  };
  return (
    <div className="flex py-4 justify-between items-center">
      <span className="flex justify-center items-center w-6 h-6 bg-gray-600 text-s text-white rounded-sm">
        E
      </span>

      {isAuth && (
        <ul className="flex gap-8">
          <li>
            <NavLink
              to={'/'}
              href="/"
              className="text-s text-gray-400 hover:text-white"
              style={({ isActive }) => (isActive ? activeStyles : undefined)}
            >
              Головна
            </NavLink>
          </li>
          <li>
            <NavLink
              to={'/posts'}
              href="/"
              className="text-s text-gray-400 hover:text-white"
              style={({ isActive }) => (isActive ? activeStyles : undefined)}
            >
              Мої пости
            </NavLink>
          </li>
          <li>
            <NavLink
              to={'/new'}
              href="/"
              className="text-s text-gray-400 hover:text-white"
              style={({ isActive }) => (isActive ? activeStyles : undefined)}
            >
              Додати пост
            </NavLink>
          </li>
        </ul>
      )}

      <div className="flex justify-center items-center bg-gray-600 text-s text-white rounded-sm px-4 py-2">
        {isAuth ? (
          <button onClick={logoutHandler}>Вийти</button>
        ) : (
          <Link to={'/login'}> Увійти </Link>
        )}
      </div>
    </div>
  );
};

```

### Структура компоненту PopularPosts.jsx
```
import React from 'react';
import { Link } from 'react-router-dom';

export const PopularPosts = ({ post }) => {
  return (
    <div className="bg-gray-600 my-1">
      <Link to={`${post._id}`}>
        <div className="flex text-xs p-2 text-gray-300 hover:bg-gray-800 hover:text-white">
          {post.title}
        </div>
      </Link>
    </div>
  );
};

```

### Структура компоненту PostItem.jsx
```
import React from 'react';
import { AiFillEye, AiOutlineMessage } from 'react-icons/ai';
import dayjs from 'dayjs';
import { Link } from 'react-router-dom';

export const PostItem = ({ post }) => {
  if (!post) {
    return (
      <div className="text-xl text-center text-white py-10">Загрузка...</div>
    );
  }
  return (
    <Link to={`/${post._id}`}>
      <div className="flex flex-col basis-1/4 flex-grow">
        <div
          className={post.imgUrl ? 'flex rouded-sm h-80' : 'flex rounded-sm'}
        >
          {post.imgUrl && (
            <img
              src={`http://localhost:3002/${post.imgUrl}`}
              alt="img"
              className="object-cover w-full"
            />
          )}
        </div>
        <div className="flex justify-between items-center pt-2">
          <div className="text-xs text-white opacity-50">{post.username}</div>
          <div className="text-xs text-white opacity-50">
            {dayjs(post.createdAt).format('DD.MM.YYYY')}
          </div>
        </div>
        <div data-testid="post-item" className="text-white text-xl">
          {post.title}
        </div>
        <p className="text-white opacity-60 text-xs pt-4 line-clamp-4">
          {post.text}
        </p>

        <div className="flex gap-3 items-center mt-2">
          <button className="flex items-center justify-center gap-2 text-xs text-white opacity-50">
            <AiFillEye /> <span>{post.views}</span>
          </button>
          <button className="flex items-center justify-center gap-2 text-xs text-white opacity-50">
            <AiOutlineMessage /> <span>{post.comments?.length || 0}</span>
          </button>
        </div>
      </div>
    </Link>
  );
};

```
## Файлова структура
![1](/assets/labs/lab-1/structure(1).jpg)
![2](/assets/labs/lab-1/structure(2).jpg)


## ЧАСТИНА 2. Налаштування середовища Node.js. Основи роботи з Express.js
У другій частині лабораторної роботи було виконано завдання зі створення базового HTTP-сервера за допомогою Node.js та фреймворку Express.js, а також реалізовано REST API для роботи з колекцією студентів.

### Завдання 1. Створення Node.js проєкту та встановлення Express
Ініціалізуємо Node.js проєкт в директорії серверної частини (lab1_app/server) за допомогою команди: 
```
npm init -y
```
та встановлюємо бібліотеку Express.js:
```
npm install express
```

### Завдання 2. Створення HTTP-сервера
Створюємо файл index.js, підключаємо Express та налаштовуємо базовий маршрут для кореневого URL (/), який повертає повідомлення.
```
const express = require('express');
const app = express();

const PORT = 3000;

app.get('/', (req, res) => {
    res.send('Hello from Node.js server');
});

app.listen(PORT, () => {
    console.log(`Server is running on http://localhost:${PORT}`);
});
```

![Повідомлення від Node.js сервера ](/assets/labs/lab-1/screenshot-message-server.png)

### Завдання 3. Маршрут GET /students
Створюємо масив об’єктів студентів (як імітацію бази даних) та реалізовуємо маршрут GET /students, який повертає цей список у форматі JSON.
```
app.use(express.json()); 

let students = [
    { id: 1, name: "Petrenko Ivan", group: "IS-31" },
    { id: 2, name: "Shevchenko Maria", group: "IS-32" },
    { id: 3, name: "Zelinskiy Ihor", group: "IS-33" },

];

app.get('/students', (req, res) => {
    res.json(students);
});

```
![Відповідь сервера GET /students ](/assets/labs/lab-1/screenshot-server-response.png)

### Завдання 4. Маршрут POST /students
Створюємо маршрут POST /students, який приймає дані у форматі JSON, перевіряє їх на наявність обов’язкових полів (id, name, group), перевіряє чи немає дублювання ідентифікатора, та додає нового студента до масиву.
```
app.post('/students', (req, res) => {
    const { id, name, group } = req.body;

    if (!id || !name || !group) {
        return res.status(400).json({
            message: "All fields (id, name, group) are required"
        });
    }

    const existingStudent = students.find(s => s.id === id);
    if (existingStudent) {
        return res.status(400).json({
            message: "Student with this id already exists"
        });
    }

    const newStudent = { id, name, group };
    students.push(newStudent);

    res.status(201).json({
        message: "Student added",
        student: newStudent
    });
});

```

### Завдання 5. PUT та DELETE
Оновлення студента: PUT /students/:id — для оновлення даних студента
```
app.put('/students/:id', (req, res) => {
    const id = parseInt(req.params.id);
    const updatedData = req.body;

    const student = students.find(s => s.id === id);

    if (!student) {
        return res.status(404).json({ message: "Student not found" });
    }

    student.name = updatedData.name || student.name;
    student.group = updatedData.group || student.group;

    res.json({
        message: "Student updated",
        student
    });
});

```
Видалення студента: DELETE /students/:id — для видалення студента
```
app.delete('/students/:id', (req, res) => {
    const id = parseInt(req.params.id);

    const index = students.findIndex(s => s.id === id);

    if (index === -1) {
        return res.status(404).json({ message: "Student not found" });
    }

    students.splice(index, 1);

    res.json({ message: "Student deleted" });
});

```
![Відпрацювання тестувань запитів API  ](/assets/labs/lab-1/screenshot-student-api-demo.png)

## Висновки

У ході виконання роботи було проаналізовано предметну область та обґрунтовано актуальність розробки веб-застосунку типу мініблогу. Визначено мету роботи, об’єкт і предмет дослідження, а також сформульовано основні завдання, необхідні для досягнення поставленої мети.

Було описано бізнес-логіку функціонування системи MiniBlog, яка визначає правила взаємодії користувачів із системою та порядок обробки інформації. Також сформовано перелік функціональних і нефункціональних вимог, що визначають можливості системи та основні характеристики її роботи.

Крім того, побудовано та описано Use Case діаграму, яка відображає взаємодію користувачів із системою та основні сценарії її використання. Також було побудовано діаграму зв'язків (ER-діагарама). Отримані результати дозволяють чітко визначити функціональність системи та слугують основою для подальшого проєктування і розвитку веб-застосунку.
