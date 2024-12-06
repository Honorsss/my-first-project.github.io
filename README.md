
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Меню Ресторана</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Arial', sans-serif;
      background-color: #f4f4f4;
      color: #333;
      line-height: 1.6;
      overflow-x: hidden; /* чтобы предотвратить горизонтальную прокрутку при анимации */
      position: relative;
    }

    /* Стили для ленты */
    .info-bar {
      background-color: #1daf00;
      color: white;
      text-align: center;
      padding: 10px;
      font-size: 16px;
      font-weight: bold;
      position: fixed;
      width: 100%;
      top: 0; 
      z-index: 1000;
      animation: slideDown 0.3s ease-out, fadeInOut 4s ease-in-out infinite; /* добавили анимацию мигания */
    }

    /* Анимация появления и исчезновения ленты */
    @keyframes slideDown {
      0% {
        top: -50px;
      }
      100% {
        top: 0;
      }
    }

    @keyframes fadeInOut {
      0%, 100% {
        opacity: 1; /* полная видимость */
      }
      50% {
        opacity: 0; /* исчезновение */
      }
    }

    header {
      background-color: #2c3e50;
      color: white;
      padding: 30px 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    }

    header .logo h1 {
      font-size: 36px;
      font-family: 'Montserrat', sans-serif;
      letter-spacing: 2px;
    }

    nav ul {
      list-style: none;
      display: flex;
    }

    nav ul li {
      margin-left: 20px;
    }

    nav ul li a {
      color: white;
      text-decoration: none;
      font-size: 18px;
      font-weight: bold;
      padding: 8px 16px;
      border-radius: 20px;
      transition: background-color 0.3s ease;
    }

    nav ul li a:hover {
      background-color: #e74c3c;
    }

    .menu-section {
      padding: 80px 20px;
      text-align: center;
      background-color: #2c3e50;
      color: white;
    }

    .menu-section h2 {
      font-size: 48px;
      margin-bottom: 50px;
      font-family: 'Montserrat', sans-serif;
    }

    .menu-items {
      display: flex;
      justify-content: space-around;
      flex-wrap: wrap;
      gap: 20px;
    }

    .menu-item {
      background-color: #fff;
      border-radius: 15px;
      box-shadow: 0 8px 12px rgba(0, 0, 0, 0.1);
      width: 280px;
      padding: 25px;
      text-align: center;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }

    .menu-item:hover {
      transform: translateY(-10px) scale(1.05);
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
    }

    .menu-item img {
      width: 100%;
      height: auto;
      border-radius: 10px;
      transition: transform 0.3s ease;
    }

    .menu-item:hover img {
      transform: scale(1.1);
    }

    .menu-item h3 {
      font-size: 22px;
      margin-top: 15px;
      color: #34495e;
    }

    .menu-item p {
      font-size: 14px;
      margin: 10px 0;
      color: #7f8c8d;
    }

    .price {
      font-size: 20px;
      font-weight: bold;
      color: #e74c3c;
    }

    footer {
      background-color: #34495e;
      color: white;
      text-align: center;
      padding: 20px;
      font-size: 14px;
    }

    .menu-item .add-to-cart {
      background-color: #e74c3c;
      color: white;
      padding: 12px 25px;
      border-radius: 25px;
      font-weight: bold;
      font-size: 16px;
      text-decoration: none;
      display: inline-block;
      transition: background-color 0.3s ease, transform 0.2s ease;
      margin-top: 15px;
    }

    .menu-item .add-to-cart:hover {
      background-color: #c0392b;
      transform: scale(1.05);
    }

    .menu-item .add-to-cart:active {
      transform: scale(0.98);
    }

    /* Анимация падающих снежинок */
    .snowflake {
      position: absolute;
      top: -10%;
      color: white;
      font-size: 24px;
      pointer-events: none;
      animation: snow 10s linear infinite;
    }

    /* Разные скорости и направление анимации снежинок */
    @keyframes snow {
      0% {
        transform: translateX(0) translateY(-10%);
      }
      100% {
        transform: translateX(100px) translateY(100vh);
      }
    }

    .snowflake:nth-child(1) {
      left: 10%;
      animation-duration: 12s;
      animation-delay: 0s;
      animation-timing-function: ease-in-out;
    }

    .snowflake:nth-child(2) {
      left: 20%;
      animation-duration: 10s;
      animation-delay: 2s;
      animation-timing-function: linear;
    }

    .snowflake:nth-child(3) {
      left: 30%;
      animation-duration: 14s;
      animation-delay: 1s;
      animation-timing-function: ease-in;
    }

    .snowflake:nth-child(4) {
      left: 40%;
      animation-duration: 16s;
      animation-delay: 3s;
      animation-timing-function: ease-out;
    }

    .snowflake:nth-child(5) {
      left: 50%;
      animation-duration: 18s;
      animation-delay: 4s;
      animation-timing-function: linear;
    }

    .snowflake:nth-child(6) {
      left: 60%;
      animation-duration: 20s;
      animation-delay: 5s;
      animation-timing-function: ease-in-out;
    }

    .snowflake:nth-child(7) {
      left: 70%;
      animation-duration: 22s;
      animation-delay: 6s;
      animation-timing-function: ease-in;
    }

    /* Стили для новогодней елки */
    .tree {
      position: absolute;
      top: 50px;
      right: 20px;
      font-size: 80px; /* Увеличено */
      animation: treeMove 10s ease-in-out infinite;
    }

    @keyframes treeMove {
      0% {
        transform: scale(1) rotate(0deg);
      }
      50% {
        transform: scale(1.2) rotate(15deg); /* Немного больше движение */
      }
      100% {
        transform: scale(1) rotate(0deg);
      }
    }

    /* Стили для подарков */
    .gift {
      position: absolute;
      width: 50px;
      height: 50px;
      background-color: #e74c3c;
      border-radius: 10px;
      animation: giftMove 8s infinite ease-in-out;
    }

    .gift::before {
      content: '';
      position: absolute;
      top: -10px;
      left: 50%;
      width: 5px;
      height: 20px;
      background-color: #fff;
      transform: translateX(-50%);
    }

    .gift:nth-child(1) {
      top: 10%;
      left: 5%;
      animation-delay: 2s;
    }

    .gift:nth-child(2) {
      top: 10%;
      right: 5%;
      animation-delay: 4s;
    }

    .gift:nth-child(3) {
      bottom: 10%;
      left: 25%;
      animation-delay: 6s;
    }

    .gift:nth-child(4) {
      bottom: 10%;
      right: 25%;
      animation-delay: 3s;
    }

    @keyframes giftMove {
      0%, 100% {
        transform: translateY(0) rotate(0deg);
      }
      50% {
        transform: translateY(20px) rotate(180deg);
      }
    }
  </style>
</head>
<body>
  <!-- Лента сверху -->
  <div class="info-bar">
    Бесплатная доставка при заказе от 1000 сом! 🎉
  </div>

  <header>
    <div class="logo">
      <h1>Ресторан "Вкусный уголок"</h1>
    </div>
    <nav>
      <ul>
        <li><a href="#">Главная</a></li>
        <li><a href="#">Меню</a></li>
        <li><a href="#">О нас</a></li>
        <li><a href="#">Контакты</a></li>
      </ul>
    </nav>
  </header>

  <!-- Падающие снежинки -->
  <div class="snowflake">❄</div>
  <div class="snowflake">❄</div>
  <div class="snowflake">❄</div>
  <div class="snowflake">❄</div>
  <div class="snowflake">❄</div>
  <div class="snowflake">❄</div>
  <div class="snowflake">❄</div>

  <!-- Новогодняя елка -->
  <div class="tree">🎄</div>

  <!-- Подарки -->
</html>
<div class="gift"></div>
  <div class="gift"></div>
  <div class="gift"></div>
  <div class="gift"></div>

  <section class="menu-section">
    <h2>Наше меню</h2>
    <div class="menu-items">
      <div class="menu-item">
        <img src="паста карбонора.jpg" alt="Паста Карбонара">
        <h3>Паста Карбонара</h3>
        <p>Паста с соусом Карбонара и пармезаном.</p>
        <span class="price">500 сом</span>
        <a href="#" class="add-to-cart">Добавить в корзину</a>
      </div>
      <div class="menu-item">
        <img src="салат цезарь.jpg" alt="Салат Цезарь">
        <h3>Салат Цезарь</h3>
        <p>Свежие листья салата, курица, сыр и соус Цезарь.</p>
        <span class="price">350 сом</span>
        <a href="#" class="add-to-cart">Добавить в корзину</a>
      </div>
      <div class="menu-item">
        <img src="стейк рибай.jpg" alt="Стейк Рибай">
        <h3>Стейк Рибай</h3>
        <p>Сочный стейк с гарниром и соусом.</p>
        <span class="price">1200 сом</span>
        <a href="#" class="add-to-cart">Добавить в корзину</a>
      </div>
    </div>

    <div class="menu-items">
      <div class="menu-item">
        <img src="суп борщ.jpg" alt="Суп Борщ">
        <h3>Суп Борщ</h3>
        <p>Классический борщ с говядиной, свеклой и сметаной.</p>
        <span class="price">300 сом</span>
        <a href="#" class="add-to-cart">Добавить в корзину</a>
      </div>
      <div class="menu-item">
        <img src="пицца маргарита.jpg" alt="Пицца Маргарита">
        <h3>Пицца Маргарита</h3>
        <p>Томаты, моцарелла, базилик, оливковое масло.</p>
        <span class="price">400 сом</span>
        <a href="#" class="add-to-cart">Добавить в корзину</a>
      </div>
      <div class="menu-item">
        <img src="тирамису.jpg" alt="Тирамису">
        <h3>Тирамису</h3>
        <p>Нежный итальянский десерт с кофе и маскарпоне.</p>
        <span class="price">350 сом</span>
        <a href="#" class="add-to-cart">Добавить в корзину</a>
      </div>
    </div>
  </section>

  <footer>
    <p>&copy; 2024 Ресторан "Вкусный уголок". Все права защищены.</p>
  </footer>
</body>
</html>
