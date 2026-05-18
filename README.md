# marrakesh.menus.github.io
Menu grill bar Marrakesh 
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>Марракеш — Меню ресторана</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', 'Roboto', Helvetica, Arial, sans-serif;
            background: #fef7e8;
            color: #2c1e12;
            padding: 20px 16px 60px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: #fffcf5;
            border-radius: 32px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            overflow: hidden;
            padding: 24px 20px 40px;
        }

        /* Header */
        .header {
            text-align: center;
            margin-bottom: 28px;
            border-bottom: 2px solid #e0c8a8;
            padding-bottom: 20px;
        }

        .header h1 {
            font-size: 2.4rem;
            letter-spacing: 2px;
            color: #b45f2b;
            font-weight: 600;
        }

        .header p {
            color: #7e5e3c;
            margin-top: 8px;
            font-style: italic;
        }

        /* QR блок */
        .qr-section {
            display: flex;
            justify-content: center;
            margin-bottom: 36px;
            background: #fff2e2;
            padding: 20px;
            border-radius: 28px;
            flex-wrap: wrap;
            align-items: center;
            gap: 24px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.03);
        }

        .qr-card {
            text-align: center;
            background: white;
            padding: 12px;
            border-radius: 24px;
            box-shadow: 0 6px 14px rgba(0,0,0,0.1);
        }

        .qr-card canvas, .qr-card img {
            width: 140px;
            height: 140px;
            display: block;
            margin: 0 auto;
        }

        .qr-text {
            font-size: 1rem;
            color: #3b2a1f;
            max-width: 260px;
        }

        .qr-text strong {
            color: #b45f2b;
        }

        .qr-note {
            font-size: 0.75rem;
            color: #9b7a56;
            margin-top: 6px;
        }

        /* навигация по категориям (быстрая) */
        .nav-cats {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin-bottom: 32px;
            background: #fdf3e6;
            padding: 12px 10px;
            border-radius: 60px;
            position: sticky;
            top: 10px;
            background: rgba(253, 243, 230, 0.95);
            backdrop-filter: blur(8px);
            z-index: 10;
        }

        .nav-cats a {
            background: #ffffffcc;
            text-decoration: none;
            font-size: 0.8rem;
            font-weight: 500;
            padding: 6px 14px;
            border-radius: 40px;
            color: #b45f2b;
            border: 1px solid #e0c8a8;
            transition: 0.2s;
        }

        .nav-cats a:hover {
            background: #b45f2b;
            color: white;
            border-color: #b45f2b;
        }

        /* категории меню */
        .menu-section {
            margin-top: 36px;
            scroll-margin-top: 80px;
        }

        .section-title {
            font-size: 1.8rem;
            font-weight: 700;
            border-left: 8px solid #b45f2b;
            padding-left: 18px;
            margin-bottom: 22px;
            color: #3b2a1f;
            letter-spacing: -0.3px;
        }

        .grid-items {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 12px 18px;
        }

        .menu-item {
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            flex-wrap: wrap;
            padding: 12px 0;
            border-bottom: 1px dashed #eedbc8;
        }

        .item-desc {
            flex: 2;
            font-size: 0.95rem;
        }

        .item-name {
            font-weight: 600;
            color: #2c1e12;
        }

        .item-details {
            font-size: 0.75rem;
            color: #8f6e48;
            margin-top: 4px;
        }

        .item-price {
            font-weight: 700;
            color: #b45f2b;
            white-space: nowrap;
            margin-left: 12px;
            font-size: 1rem;
        }

        .subsection {
            margin-top: 20px;
            margin-bottom: 12px;
            font-weight: 600;
            font-size: 1.3rem;
            color: #996633;
            padding-left: 8px;
            border-left: 4px solid #e0b082;
        }

        .two-col {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 4px 20px;
        }

        .note {
            background: #f7efE4;
            padding: 12px 18px;
            border-radius: 20px;
            font-size: 0.8rem;
            color: #866633;
            margin: 20px 0;
            text-align: center;
        }

        footer {
            margin-top: 48px;
            text-align: center;
            font-size: 0.7rem;
            color: #b49673;
            border-top: 1px solid #eedbc8;
            padding-top: 24px;
        }

        @media (max-width: 640px) {
            .container {
                padding: 16px;
            }
            .section-title {
                font-size: 1.5rem;
            }
            .menu-item {
                flex-direction: column;
                align-items: flex-start;
                gap: 6px;
            }
            .item-price {
                margin-left: 0;
                align-self: flex-end;
            }
        }
    </style>
</head>
<body>
<div class="container">
    <div class="header">
        <h1>МАРРАКЕШ</h1>
        <p>восточная & европейская кухня • авторская карта напитков</p>
    </div>

    <!-- БЛОК QR-КОДА динамический -->
    <div class="qr-section" id="qrBlock">
        <div class="qr-card" id="qrcodeContainer"></div>
        <div class="qr-text">
            <strong>📱 Отсканируйте QR-код</strong><br>
            Откроет это меню на вашем телефоне.<br>
            <span class="qr-note">Меню всегда актуально — добавьте в закладки</span>
        </div>
    </div>

    <!-- быстрые ссылки -->
    <div class="nav-cats">
        <a href="#section-drinks">🍸 Настойки</a>
        <a href="#section-wine">🍷 Вина</a>
        <a href="#section-salads">🥗 Салаты</a>
        <a href="#section-soups">🍲 Супы</a>
        <a href="#section-pasta">🍝 Паста</a>
        <a href="#section-main">🍛 Основное</a>
        <a href="#section-grill">🔥 Гриль/Море</a>
        <a href="#section-deserts">🍰 Десерты</a>
    </div>

    <!-- ======================= НАПИТКИ ======================= -->
    <div id="section-drinks" class="menu-section">
        <div class="section-title">🍸 Настойки & Крепкий бар</div>
        <div class="subsection">Настойки и дистилляты (40 мл)</div>
        <div class="grid-items">
            <div class="menu-item"><div class="item-desc"><span class="item-name">Бехеровка</span><div class="item-details">Чехия, 38%</div></div><div class="item-price">410 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Кампари</span><div class="item-details">Италия, 24%</div></div><div class="item-price">420 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Апероль</span><div class="item-details">Италия, 11%</div></div><div class="item-price">420 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Самбука</span><div class="item-details">Италия, 40%</div></div><div class="item-price">420 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Абсент Luxardo</span><div class="item-details">Италия, 70%</div></div><div class="item-price">420 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Ягермейстер</span><div class="item-details">Германия, 35%</div></div><div class="item-price">420 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Ча Ча</span><div class="item-details">Россия, 40%</div></div><div class="item-price">280 ₽</div></div>
        </div>
        <div class="subsection">Ягодные настойки Онегин Gourmet (40 мл)</div>
        <div class="grid-items">
            <div class="menu-item"><div class="item-desc"><span class="item-name">Черноплодная рябина</span><div class="item-details">20%</div></div><div class="item-price">350 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Чёрная смородина</span><div class="item-details">20%</div></div><div class="item-price">350 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Вишня</span><div class="item-details">20%</div></div><div class="item-price">350 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Грейпфрут</span><div class="item-details">20%</div></div><div class="item-price">350 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Сет из 4 настоек</span><div class="item-details">4 по 25 мл</div></div><div class="item-price">820 ₽</div></div>
        </div>
        <div class="subsection">Водка (40 мл)</div>
        <div class="grid-items">
            <div class="menu-item"><div class="item-desc"><span class="item-name">Онегин</span><div class="item-details">Россия, 40%</div></div><div class="item-price">310 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Чистые Росы</span><div class="item-details">Россия, 40%</div></div><div class="item-price">350 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Зерно</span><div class="item-details">Россия, 40%</div></div><div class="item-price">220 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Мамонт</span><div class="item-details">Россия, 40%</div></div><div class="item-price">260 ₽</div></div>
        </div>
        <div class="subsection">Вермуты (100 мл)</div>
        <div class="grid-items">
            <div class="menu-item"><div class="item-desc"><span class="item-name">Чинзано Bianco</span><div class="item-details">Италия, 15%</div></div><div class="item-price">420 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Чинзано Rosso</span><div class="item-details">Италия, 15%</div></div><div class="item-price">420 ₽</div></div>
        </div>
        <div class="subsection">Виски, джин, текила (40 мл)</div>
        <div class="grid-items">
            <div class="menu-item"><div class="item-desc"><span class="item-name">Джемессон</span><div class="item-details">Ирландия, 40%</div></div><div class="item-price">210 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Баллантайнс</span><div class="item-details">Шотландия, 40%</div></div><div class="item-price">210 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Джек Дэниелс</span><div class="item-details">США, 40%</div></div><div class="item-price">210 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Чивас Ригал 12 лет</span><div class="item-details">Шотландия, 40%</div></div><div class="item-price">210 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Макаллан Дабл Каск 12 лет</span><div class="item-details">Шотландия, 40%</div></div><div class="item-price">1800 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Хопперс джин</span><div class="item-details">Россия, 40%</div></div><div class="item-price">420 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Ольмека Бланко</span><div class="item-details">Мексика, 38% + лайм</div></div><div class="item-price">470 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Ольмека Голд</span><div class="item-details">Мексика, 38%</div></div><div class="item-price">470 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Curado Blue Agave</span><div class="item-details">Мексика, 40%</div></div><div class="item-price">740 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Olmeca Altos Reposado</span><div class="item-details">Мексика, 40%</div></div><div class="item-price">740 ₽</div></div>
        </div>
        <div class="subsection">Ром / Коньяк / Бренди (40 мл)</div>
        <div class="grid-items">
            <div class="menu-item"><div class="item-desc"><span class="item-name">Гавана Клуб Аньехо 3 года</span><div class="item-details">Куба, 40%</div></div><div class="item-price">480 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Бакарди Карта Негра</span><div class="item-details">США, 37%</div></div><div class="item-price">480 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Матисс 3*</span><div class="item-details">Армения, 40%</div></div><div class="item-price">250 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Матисс 5*</span><div class="item-details">Армения, 40%</div></div><div class="item-price">270 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Коктебель 5 лет</span><div class="item-details">Крым, 40%</div></div><div class="item-price">250 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Camus VS</span><div class="item-details">Франция, 40%</div></div><div class="item-price">720 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Camus VSOP</span><div class="item-details">Франция, 40%</div></div><div class="item-price">870 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Merlet XO</span><div class="item-details">Франция, 40%</div></div><div class="item-price">1740 ₽</div></div>
        </div>
        <div class="subsection">Пиво разливное (0,4 л / 0,5 л) </div>
        <div class="grid-items">
            <div class="menu-item"><div class="item-desc"><span class="item-name">Паулайнер (нефильтрованное)</span><div class="item-details">Германия</div></div><div class="item-price">870 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Будвайзер светлое</span><div class="item-details">Чехия</div></div><div class="item-price">720 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Паулайнер безалкогольное</span><div class="item-details"></div></div><div class="item-price">720 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Крушовица</span><div class="item-details"></div></div><div class="item-price">720 ₽</div></div>
        </div>
    </div>

    <!-- ======================= ВИННАЯ КАРТА ======================= -->
    <div id="section-wine" class="menu-section">
        <div class="section-title">🍷 Вина & Игристое</div>
        <div class="subsection">Игристые вина (бокал 150 мл / бутылка 750 мл)</div>
        <div class="grid-items">
            <div class="menu-item"><div class="item-desc"><span class="item-name">Просекко Бруни</span><div class="item-details">Италия, сухое</div></div><div class="item-price">330₽ / 3300₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Просекко Бруни Розе</span><div class="item-details">Италия, розе</div></div><div class="item-price">330₽ / 3300₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Балаклава брют</span><div class="item-details">Россия, 11,5%</div></div><div class="item-price">330₽ / 1800₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Балаклава полусладкое</span><div class="item-details">Россия</div></div><div class="item-price">330₽ / 1800₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Moet & Chandon Imperial</span><div class="item-details">Белое сухое, Франция</div></div><div class="item-price">18000₽ (бут.)</div></div>
        </div>
        <div class="subsection">Вино по бокалам (150 мл)</div>
        <div class="grid-items">
            <div class="menu-item"><div class="item-desc"><span class="item-name">Нуволе Бьянко Шардоне</span><div class="item-details">Россия, сухое</div></div><div class="item-price">330 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Мысхако Алиготе Вионье</span><div class="item-details">полусладкое белое</div></div><div class="item-price">360 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Нуволе Мерло Каберне</span><div class="item-details">красное сухое</div></div><div class="item-price">330 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Киндзмараули</span><div class="item-details">Грузия, полусладкое</div></div><div class="item-price">420 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Алазанская долина</span><div class="item-details">белое полусладкое</div></div><div class="item-price">420 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Саперави сухое</span><div class="item-details">Грузия</div></div><div class="item-price">420 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Цинандали сухое</span><div class="item-details">Грузия</div></div><div class="item-price">420 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Ханс Баер Рислинг</span><div class="item-details">полусухое, 11,5%</div></div><div class="item-price">620 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Ханс Баер Пино Нуар</span><div class="item-details">красное сухое</div></div><div class="item-price">620 ₽</div></div>
        </div>
        <div class="note">🍾 Винодельня Галицкий и Галицкий: Мерло Красная Горка, Шардоне Красная Горка, Розе — 7800₽/бут. Уточняйте у сомелье.</div>
    </div>

    <!-- ======================= САЛАТЫ ======================= -->
    <div id="section-salads" class="menu-section">
        <div class="section-title">🥗 Салаты</div>
        <div class="grid-items">
            <div class="menu-item"><div class="item-desc"><span class="item-name">Салат с рукколой и креветками</span><div class="item-details">авокадо, черри, тигровые креветки</div></div><div class="item-price">810 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Стейк-салат с говядиной</span><div class="item-details">говяжья вырезка, овощи гриль, фирменный соус</div></div><div class="item-price">920 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><span class="item-name">Теплый салат с морепродуктами</span><div class="item-details">креветки, мидии, кальмары, горчица с цитрусом</div></div><div class="item-price">940 ₽</div></div>
            <div class="menu-item"><div class="item-desc"><sp