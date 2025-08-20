
<html lang="tr" dir="ltr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lezzet Durağı - Dijital Menü</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/magnific-popup.js/1.1.0/magnific-popup.min.css">
    <style>
        /* Temel Stiller */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary-color: #e74c3c;
            --secondary-color: #f39c12;
            --dark-color: #2c3e50;
            --light-color: #ecf0f1;
            --success-color: #2ecc71;
            --info-color: #3498db;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --transition: all 0.5s cubic-bezier(0.25, 0.8, 0.25, 1);
        }

        body {
            background-color: #f5f5f5;
            color: #333;
            overflow-x: hidden;
        }

        html[lang="ar"] body {
            direction: rtl;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: white;
            padding: 1.5rem;
            text-align: center;
            position: relative;
            box-shadow: var(--shadow);
            z-index: 100;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            flex-wrap: wrap;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            display: flex;
            align-items: center;
        }

        .logo i {
            margin-right: 10px;
        }

        html[lang="ar"] .logo i {
            margin-right: 0;
            margin-left: 10px;
        }

        /* Dil Seçenekleri */
        .lang-selector {
            display: flex;
            gap: 10px;
            align-items: center;
        }

        .lang-flag {
            width: 30px;
            height: 20px;
            cursor: pointer;
            transition: var(--transition);
            border: 2px solid transparent;
            object-fit: cover;
            border-radius: 2px;
        }

        .lang-flag:hover, .lang-flag.active {
            transform: scale(1.15);
            border-color: white;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.2);
        }

        /* Duyurular Butonu */
        .announcement-btn {
            background: var(--info-color);
            border: none;
            color: white;
            padding: 0.8rem 1.5rem;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 10px;
            margin: 1rem auto;
            transition: var(--transition);
            max-width: 300px;
        }

        .announcement-btn:hover {
            background: darken(var(--info-color), 10%);
            transform: translateY(-3px);
            box-shadow: 0 4px 8px rgba(52, 152, 219, 0.3);
        }

        /* Duyurular */
        .announcement-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 1rem;
        }

        .announcement-box {
            background: white;
            border-radius: 10px;
            padding: 1.5rem;
            margin-bottom: 2rem;
            box-shadow: var(--shadow);
            animation: slideInDown 0.6s ease-out;
            display: none;
        }

        .announcement-title {
            font-size: 1.3rem;
            margin-bottom: 1rem;
            color: var(--primary-color);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .announcement-title i {
            color: var(--secondary-color);
        }

        .announcement-list {
            list-style: none;
        }

        .announcement-list li {
            background: #f8f9fa;
            border-left: 4px solid var(--info-color);
            padding: 1rem;
            margin-top: 1rem;
            border-radius: 0 5px 5px 0;
        }

        html[lang="ar"] .announcement-list li {
            border-left: none;
            border-right: 4px solid var(--info-color);
            text-align: right;
        }

        @keyframes slideInDown {
            from { transform: translateY(-30px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        /* Kategori Navigasyon */
        .category-nav {
            display: flex;
            overflow-x: auto;
            padding: 1rem;
            background: white;
            position: sticky;
            top: 0;
            z-index: 90;
            box-shadow: var(--shadow);
            scrollbar-width: none;
        }

        .category-nav::-webkit-scrollbar {
            display: none;
        }

        .category-btn {
            background: none;
            border: none;
            padding: 0.5rem 1.5rem;
            margin: 0 5px;
            border-radius: 20px;
            cursor: pointer;
            white-space: nowrap;
            transition: var(--transition);
            font-weight: bold;
            color: var(--dark-color);
        }

        .category-btn.active {
            background: var(--primary-color);
            color: white;
            transform: translateY(-3px);
            box-shadow: 0 4px 8px rgba(231, 76, 60, 0.3);
        }

        .category-btn i {
            margin-right: 8px;
        }

        html[lang="ar"] .category-btn i {
            margin-right: 0;
            margin-left: 8px;
        }

        /* Menü İçeriği */
        main {
            max-width: 1200px;
            margin: 0 auto;
            padding: 1rem;
        }

        .menu-section {
            margin-bottom: 2rem;
            animation: fadeIn 0.8s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .section-title {
            font-size: 1.8rem;
            margin-bottom: 1.5rem;
            color: var(--dark-color);
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            border-radius: 3px;
        }

        .section-title i {
            margin-right: 15px;
            color: var(--primary-color);
        }

        html[lang="ar"] .section-title i {
            margin-right: 0;
            margin-left: 15px;
        }

        .menu-items {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 2rem;
        }

        /* Mobile Responsiveness */
        @media (max-width: 768px) {
            .menu-items.horizontal-scroll {
                display: flex;
                overflow-x: auto;
                flex-wrap: nowrap;
                gap: 1rem;
                padding-bottom: 1rem;
                scroll-snap-type: x proximity;
                -webkit-overflow-scrolling: touch;
                scroll-behavior: smooth;
            }

            .menu-items.horizontal-scroll .menu-item {
                flex: 0 0 80vw;
                scroll-snap-align: center;
                max-width: 300px;
            }

            .menu-items:not(.horizontal-scroll) {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            }
        }

        @media (max-width: 480px) {
            .menu-items:not(.horizontal-scroll) {
                grid-template-columns: 1fr;
            }
        }

        /* Menü Öğeleri */
        .menu-item {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
            cursor: pointer;
            position: relative;
            transform-style: preserve-3d;
            perspective: 1000px;
        }

        .menu-item:hover {
            transform: translateY(-10px) rotateX(5deg);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
        }

        .item-image {
            height: 220px;
            overflow: hidden;
            position: relative;
        }

        .item-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }

        .menu-item:hover .item-image img {
            transform: scale(1.1) rotate(1deg);
        }

        .item-badge {
            position: absolute;
            top: 15px;
            right: 15px;
            background: var(--success-color);
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: bold;
            z-index: 2;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }

        html[lang="ar"] .item-badge {
            right: auto;
            left: 15px;
        }

        .item-content {
            padding: 1.8rem;
        }

        .item-title {
            font-size: 1.4rem;
            margin-bottom: 1rem;
            color: var(--dark-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .item-price {
            color: var(--primary-color);
            font-weight: bold;
            font-size: 1.3rem;
        }

        .item-desc {
            color: #666;
            margin-bottom: 1.5rem;
            font-size: 1rem;
            line-height: 1.6;
        }

        .item-desc-en, .item-desc-ar {
            display: none;
        }

        html[lang="tr"] .item-desc-tr,
        html[lang="en"] .item-desc-en,
        html[lang="ar"] .item-desc-ar {
            display: block;
        }

        html[lang="ar"] .item-desc-ar {
            text-align: right;
            direction: rtl;
        }

        /* Hakkımızda */
        .about-section {
            background: white;
            border-radius: 15px;
            padding: 2.5rem;
            margin: 3rem auto;
            box-shadow: var(--shadow);
            text-align: center;
            max-width: 800px;
            animation: fadeInUp 1s ease;
        }

        .about-section h2 {
            font-size: 2rem;
            margin-bottom: 1.5rem;
            color: var(--dark-color);
            position: relative;
            display: inline-block;
        }

        .about-section h2::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: var(--primary-color);
            border-radius: 2px;
        }

        .about-section p {
            font-size: 1.1rem;
            line-height: 1.8;
            color: #555;
            margin-bottom: 1.5rem;
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(50px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Animasyonlar */
        .slide-in-left {
            animation: slideInLeft 0.8s ease-out forwards;
        }

        @keyframes slideInLeft {
            from { opacity: 0; transform: translateX(-80px) rotateY(20deg); }
            to { opacity: 1; transform: translateX(0) rotateY(0); }
        }

        .slide-in-right {
            animation: slideInRight 0.8s ease-out forwards;
        }

        @keyframes slideInRight {
            from { opacity: 0; transform: translateX(80px) rotateY(-20deg); }
            to { opacity: 1; transform: translateX(0) rotateY(0); }
        }

        /* Büyütme Efekti için */
        .image-zoom {
            cursor: zoom-in;
            display: block;
            height: 100%;
        }
    </style>
</head>
<body>
    <header>
        <div class="header-content">
            <div class="logo">
                <i class="fas fa-utensils"></i>
                <span class="tr">Lezzet Durağı</span>
                <span class="en" style="display: none;">Flavor Stop</span>
                <span class="ar" style="display: none;">محطة النكهات</span>
            </div>
            <div class="lang-selector">
                <img src="https://flagcdn.com/w40/tr.png" class="lang-flag active" onclick="changeLanguage('tr')" title="Türkçe">
                <img src="https://flagcdn.com/w40/gb.png" class="lang-flag" onclick="changeLanguage('en')" title="English">
                <img src="https://flagcdn.com/w40/sa.png" class="lang-flag" onclick="changeLanguage('ar')" title="العربية">
            </div>
        </div>
    </header>

    <div class="announcement-container">
        <button class="announcement-btn">
            <i class="fas fa-bullhorn"></i>
            <span class="tr">Duyurular</span>
            <span class="en" style="display: none;">Announcements</span>
            <span class="ar" style="display: none;">إعلانات</span>
        </button>
        <div class="announcement-box">
            <h3 class="announcement-title">
                <i class="fas fa-info-circle"></i>
                <span class="tr">Güncel Duyurular</span>
                <span class="en" style="display: none;">Current Announcements</span>
                <span class="ar" style="display: none;">الإعلانات الحالية</span>
            </h3>
            <ul class="announcement-list">
                <li>
                    <strong class="tr">ÜCRETSİZ WIFI:</strong> <span class="tr">KAFE2024</span>
                    <strong class="en" style="display: none;">FREE WIFI:</strong> <span class="en" style="display: none;">KAFE2024</span>
                    <strong class="ar" style="display: none;">واي فاي مجاني:</strong> <span class="ar" style="display: none;">KAFE2024</span>
                    <p class="tr">Hızlı ve güvenli internet bağlantımız ile rahatça çalışın veya sosyal medyanızı kullanın.</p>
                    <p class="en" style="display: none;">With our fast and secure internet connection, comfortably work or use your social media.</p>
                    <p class="ar" style="display: none;">مع اتصالنا السريع والآمن بالإنترنت، اعمل براحة أو استخدم وسائل التواصل الاجتماعي الخاصة بك.</p>
                </li>
                <li>
                    <strong class="tr">Çay Bedava!</strong> <span class="tr">Tüm yemeklerle sınırsız çay ücretsiz.</span>
                    <strong class="en" style="display: none;">Free Tea!</strong> <span class="en" style="display: none;">Unlimited tea free with all meals.</span>
                    <strong class="ar" style="display: none;">شاي مجاني!</strong> <span class="ar" style="display: none;">شاي غير محدود مجانًا مع جميع الوجبات.</span>
                    <p class="tr">Lezzetli çaylarımızı deneyin, ekstra ücret yok!</p>
                    <p class="en" style="display: none;">Try our delicious teas, no extra charge!</p>
                    <p class="ar" style="display: none;">جرب شاينا اللذيذ، بدون رسوم إضافية!</p>
                </li>
                <li>
                    <strong class="tr">Hafta Sonu İndirimi:</strong> <span class="tr">%20 indirim tüm kahvaltılarda.</span>
                    <strong class="en" style="display: none;">Weekend Discount:</strong> <span class="en" style="display: none;">20% off all breakfasts.</span>
                    <strong class="ar" style="display: none;">خصم نهاية الأسبوع:</strong> <span class="ar" style="display: none;">20% خصم على جميع الفطور.</span>
                    <p class="tr">Cumartesi ve Pazar günleri geçerlidir.</p>
                    <p class="en" style="display: none;">Valid on Saturdays and Sundays.</p>
                    <p class="ar" style="display: none;">صالح يومي السبت والأحد.</p>
                </li>
            </ul>
        </div>
    </div>

    <nav class="category-nav">
        <button class="category-btn active" data-category="popular">
            <i class="fas fa-fire"></i>
            <span class="tr">En Çok Sevilenler</span>
            <span class="en" style="display: none;">Most Popular</span>
            <span class="ar" style="display: none;">الأكثر شهرة</span>
        </button>
        <button class="category-btn" data-category="breakfast">
            <i class="fas fa-egg"></i>
            <span class="tr">Kahvaltı</span>
            <span class="en" style="display: none;">Breakfast</span>
            <span class="ar" style="display: none;">فطور</span>
        </button>
        <button class="category-btn" data-category="main-courses">
            <i class="fas fa-drumstick-bite"></i>
            <span class="tr">Ana Yemekler</span>
            <span class="en" style="display: none;">Main Courses</span>
            <span class="ar" style="display: none;">الوجبات الرئيسية</span>
        </button>
        <button class="category-btn" data-category="drinks">
            <i class="fas fa-glass-martini-alt"></i>
            <span class="tr">İçecekler</span>
            <span class="en" style="display: none;">Drinks</span>
            <span class="ar" style="display: none;">مشروبات</span>
        </button>
    </nav>

    <main>
        <!-- En Çok Sevilenler Bölümü -->
        <section class="menu-section" id="popular">
            <h2 class="section-title">
                <i class="fas fa-crown"></i>
                <span class="tr">En Çok Sevilenler</span>
                <span class="en" style="display: none;">Most Popular</span>
                <span class="ar" style="display: none;">الأكثر شهرة</span>
            </h2>
            <div class="menu-items horizontal-scroll">
                <!-- Öğe 1 -->
                <div class="menu-item slide-in-left">
                    <div class="item-image">
                        <a href="https://images.unsplash.com/photo-1551963831-b3b1ca40c98e?ixlib=rb-1.2.1&auto=format&fit=crop&w=1000&q=80" class="image-zoom">
                            <img src="https://images.unsplash.com/photo-1551963831-b3b1ca40c98e?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Serpme Kahvaltı">
                        </a>
                        <span class="item-badge tr">Özel</span>
                        <span class="item-badge en" style="display: none;">Special</span>
                        <span class="item-badge ar" style="display: none;">خاص</span>
                    </div>
                    <div class="item-content">
                        <h3 class="item-title">
                            <span class="tr">Serpme Kahvaltı</span>
                            <span class="en" style="display: none;">Turkish Breakfast</span>
                            <span class="ar" style="display: none;">فطور تركي</span>
                            <span class="item-price">₺149.99</span>
                        </h3>
                        <p class="item-desc item-desc-tr">
                            Geleneksel Türk serpme kahvaltısı: çeşitli peynirler, zeytin, yumurta, domates, salatalık, bal, kaymak ve taze ekmek.
                        </p>
                        <p class="item-desc item-desc-en" style="display: none;">
                            Traditional Turkish breakfast with assorted cheeses, olives, eggs, tomatoes, cucumbers, honey, cream and fresh bread.
                        </p>
                        <p class="item-desc item-desc-ar" style="display: none;">
                            فطور تركي تقليدي مع تشكيلة من الجبن والزيتون والبيض والطماطم والخيار والعسل والقشطة والخبز الطازج.
                        </p>
                    </div>
                </div>

                <!-- Öğe 2 -->
                <div class="menu-item slide-in-right">
                    <div class="item-image">
                        <a href="https://images.unsplash.com/photo-1568901346375-23c9450c58cd?ixlib=rb-1.2.1&auto=format&fit=crop&w=1000&q=80" class="image-zoom">
                            <img src="https://images.unsplash.com/photo-1568901346375-23c9450c58cd?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Burger">
                        </a>
                    </div>
                    <div class="item-content">
                        <h3 class="item-title">
                            <span class="tr">Özel Burger</span>
                            <span class="en" style="display: none;">Special Burger</span>
                            <span class="ar" style="display: none;">برجر خاص</span>
                            <span class="item-price">₺129.99</span>
                        </h3>
                        <p class="item-desc item-desc-tr">
                            %100 dana eti, cheddar peyniri, özel sos, marul, domates ve taze ekmek ile hazırlanmış nefis burger.
                        </p>
                        <p class="item-desc item-desc-en" style="display: none;">
                            Delicious burger prepared with 100% beef, cheddar cheese, special sauce, lettuce, tomato and fresh bread.
                        </p>
                        <p class="item-desc item-desc-ar" style="display: none;">
                            برجر لذيذ معد بلحم بقري 100٪ وجبنة شيدر وصلصة خاصة وخس وطماطم وخبز طازج.
                        </p>
                    </div>
                </div>

                <!-- Öğe 3 -->
                <div class="menu-item slide-in-left">
                    <div class="item-image">
                        <a href="https://images.unsplash.com/photo-1601050690597-df0568f70950?ixlib=rb-1.2.1&auto=format&fit=crop&w=1000&q=80" class="image-zoom">
                            <img src="https://images.unsplash.com/photo-1601050690597-df0568f70950?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Kebap">
                        </a>
                    </div>
                    <div class="item-content">
                        <h3 class="item-title">
                            <span class="tr">Adana Kebap</span>
                            <span class="en" style="display: none;">Adana Kebab</span>
                            <span class="ar" style="display: none;">كباب أضنا</span>
                            <span class="item-price">₺159.99</span>
                        </h3>
                        <p class="item-desc item-desc-tr">
                            Geleneksel Adana usulü kebap, közde biber ve domates ile servis edilir.
                        </p>
                        <p class="item-desc item-desc-en" style="display: none;">
                            Traditional Adana style kebab, served with grilled peppers and tomatoes.
                        </p>
                        <p class="item-desc item-desc-ar" style="display: none;">
                            كباب أضنة على الطريقة التقليدية، يقدم مع فلفل وطماطم مشوية.
                        </p>
                    </div>
                </div>

                <!-- Öğe 4 -->
                <div class="menu-item slide-in-right">
                    <div class="item-image">
                        <a href="https://images.unsplash.com/photo-1565299624946-b28f40a0ae38?ixlib=rb-1.2.1&auto=format&fit=crop&w=1000&q=80" class="image-zoom">
                            <img src="https://images.unsplash.com/photo-1565299624946-b28f40a0ae38?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Pizza">
                        </a>
                    </div>
                    <div class="item-content">
                        <h3 class="item-title">
                            <span class="tr">Karışık Pizza</span>
                            <span class="en" style="display: none;">Mixed Pizza</span>
                            <span class="ar" style="display: none;">بيتزا متنوعة</span>
                            <span class="item-price">₺139.99</span>
                        </h3>
                        <p class="item-desc item-desc-tr">
                            Sucuk, salam, mantar, mısır, zeytin ve bol peynirle hazırlanmış nefis pizza.
                        </p>
                        <p class="item-desc item-desc-en" style="display: none;">
                            Delicious pizza prepared with sausage, salami, mushrooms, corn, olives and plenty of cheese.
                        </p>
                        <p class="item-desc item-desc-ar" style="display: none;">
                            بيتزا لذيذة معدّة بالسجق والسلامي والفطر والذرة والزيتون والكثير من الجبن.
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Kahvaltı Bölümü -->
        <section class="menu-section" id="breakfast" style="display: none;">
            <h2 class="section-title">
                <i class="fas fa-egg"></i>
                <span class="tr">Kahvaltı</span>
                <span class="en" style="display: none;">Breakfast</span>
                <span class="ar" style="display: none;">فطور</span>
            </h2>
            <div class="menu-items horizontal-scroll">
                <!-- Kahvaltı Öğe 1 -->
                <div class="menu-item slide-in-left">
                    <div class="item-image">
                        <a href="https://images.unsplash.com/photo-1626082910499-e37f5adcdedb?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80" class="image-zoom">
                            <img src="https://images.unsplash.com/photo-1626082910499-e37f5adcdedb?ixlib=rb-4.0.3&auto=format&fit=crop&w=500&q=80" alt="Menemen">
                        </a>
                        <span class="item-badge tr">Klasik</span>
                        <span class="item-badge en" style="display: none;">Classic</span>
                        <span class="item-badge ar" style="display: none;">كلاسيكي</span>
                    </div>
                    <div class="item-content">
                        <h3 class="item-title">
                            <span class="tr">Menemen</span>
                            <span class="en" style="display: none;">Menemen</span>
                            <span class="ar" style="display: none;">منيمن</span>
                            <span class="item-price">₺89.99</span>
                        </h3>
                        <p class="item-desc item-desc-tr">
                            Taze domates, biber ve yumurta ile hazırlanmış geleneksel Türk menemen.
                        </p>
                        <p class="item-desc item-desc-en" style="display: none;">
                            Traditional Turkish menemen prepared with fresh tomatoes, peppers and eggs.
                        </p>
                        <p class="item-desc item-desc-ar" style="display: none;">
                            منيمن تركي تقليدي معد من الطماطم الطازجة والفلفل والبيض.
                        </p>
                    </div>
                </div>

                <!-- Kahvaltı Öğe 2 -->
                <div class="menu-item slide-in-right">
                    <div class="item-image">
                        <a href="https://images.unsplash.com/photo-1528207776513-c1f8901a4862?ixlib=rb-1.2.1&auto=format&fit=crop&w=1000&q=80" class="image-zoom">
                            <img src="https://images.unsplash.com/photo-1528207776513-c1f8901a4862?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Omlet">
                        </a>
                    </div>
                    <div class="item-content">
                        <h3 class="item-title">
                            <span class="tr">Peynirli Omlet</span>
                            <span class="en" style="display: none;">Cheese Omelette</span>
                            <span class="ar" style="display: none;">أومليت بالجبن</span>
                            <span class="item-price">₺79.99</span>
                        </h3>
                        <p class="item-desc item-desc-tr">
                            Bol peynirli, taze otlarla zenginleştirilmiş yumuşak omlet.
                        </p>
                        <p class="item-desc item-desc-en" style="display: none;">
                            Soft omelette enriched with plenty of cheese and fresh herbs.
                        </p>
                        <p class="item-desc item-desc-ar" style="display: none;">
                            أومليت ناعم غني بالكثير من الجبن والأعشاب الطازجة.
                        </p>
                    </div>
                </div>

                <!-- Kahvaltı Öğe 3 -->
                <div class="menu-item slide-in-left">
                    <div class="item-image">
                        <a href="https://images.unsplash.com/photo-1559056199-2cdaa3194d4d?ixlib=rb-1.2.1&auto=format&fit=crop&w=1000&q=80" class="image-zoom">
                            <img src="https://images.unsplash.com/photo-1559056199-2cdaa3194d4d?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Sahanda Yumurta">
                        </a>
                    </div>
                    <div class="item-content">
                        <h3 class="item-title">
                            <span class="tr">Sahanda Yumurta</span>
                            <span class="en" style="display: none;">Fried Eggs</span>
                            <span class="ar" style="display: none;">بيض مقلي</span>
                            <span class="item-price">₺69.99</span>
                        </h3>
                        <p class="item-desc item-desc-tr">
                            Tereyağında kızartılmış taze yumurtalar, sucuk veya pastırma ile.
                        </p>
                        <p class="item-desc item-desc-en" style="display: none;">
                            Fresh eggs fried in butter, with sausage or pastrami.
                        </p>
                        <p class="item-desc item-desc-ar" style="display: none;">
                            بيض طازج مقلي في الزبدة، مع السجق أو الباستيرما.
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Ana Yemekler Bölümü -->
        <section class="menu-section" id="main-courses" style="display: none;">
            <h2 class="section-title">
                <i class="fas fa-drumstick-bite"></i>
                <span class="tr">Ana Yemekler</span>
                <span class="en" style="display: none;">Main Courses</span>
                <span class="ar" style="display: none;">الوجبات الرئيسية</span>
            </h2>
            <div class="menu-items">
                <!-- Ana Yemek Öğe 1 -->
                <div class="menu-item slide-in-left">
                    <div class="item-image">
                        <a href="https://images.unsplash.com/photo-1630170766114-9f714e880e30?ixlib=rb-1.2.1&auto=format&fit=crop&w=1000&q=80" class="image-zoom">
                            <img src="https://images.unsplash.com/photo-1630170766114-9f714e880e30?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="İskender Kebap">
                        </a>
                    </div>
                    <div class="item-content">
                        <h3 class="item-title">
                            <span class="tr">İskender Kebap</span>
                            <span class="en" style="display: none;">Iskender Kebab</span>
                            <span class="ar" style="display: none;">كباب إسكندر</span>
                            <span class="item-price">₺169.99</span>
                        </h3>
                        <p class="item-desc item-desc-tr">
                            Döner eti, pide, yoğurt ve tereyağı sosu ile servis edilen klasik İskender.
                        </p>
                        <p class="item-desc item-desc-en" style="display: none;">
                            Classic Iskender served with doner meat, pita, yogurt and butter sauce.
                        </p>
                        <p class="item-desc item-desc-ar" style="display: none;">
                            إسكندر كلاسيكي يقدم مع لحم الدونر والخبز والزبادي وصلصة الزبدة.
                        </p>
                    </div>
                </div>

                <!-- Ana Yemek Öğe 2 -->
                <div class="menu-item slide-in-right">
                    <div class="item-image">
                        <a href="https://images.unsplash.com/photo-1562966096-7c81174dd6ea?ixlib=rb-1.2.1&auto=format&fit=crop&w=1000&q=80" class="image-zoom">
                            <img src="https://images.unsplash.com/photo-1562966096-7c81174dd6ea?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Lahmacun">
                        </a>
                    </div>
                    <div class="item-content">
                        <h3 class="item-title">
                            <span class="tr">Lahmacun</span>
                            <span class="en" style="display: none;">Lahmacun</span>
                            <span class="ar" style="display: none;">لحماجون</span>
                            <span class="item-price">₺59.99</span>
                        </h3>
                        <p class="item-desc item-desc-tr">
                            İnce hamur üzerine kıyma, soğan ve baharat karışımı ile fırınlanmış lahmacun.
                        </p>
                        <p class="item-desc item-desc-en" style="display: none;">
                            Lahmacun baked with minced meat, onion and spice mixture on thin dough.
                        </p>
                        <p class="item-desc item-desc-ar" style="display: none;">
                            لحماجون مخبوز مع خليط اللحم المفروم والبصل والتوابل على عجينة رقيقة.
                        </p>
                    </div>
                </div>

                <!-- Ana Yemek Öğe 3 -->
                <div class="menu-item slide-in-left">
                    <div class="item-image">
                        <a href="https://images.unsplash.com/photo-1619682825361-e2094657e0a0?ixlib=rb-1.2.1&auto=format&fit=crop&w=1000&q=80" class="image-zoom">
                            <img src="https://images.unsplash.com/photo-1619682825361-e2094657e0a0?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Tavuk Şiş">
                        </a>
                    </div>
                    <div class="item-content">
                        <h3 class="item-title">
                            <span class="tr">Tavuk Şiş</span>
                            <span class="en" style="display: none;">Chicken Shish</span>
                            <span class="ar" style="display: none;">شيش طاووق</span>
                            <span class="item-price">₺129.99</span>
                        </h3>
                        <p class="item-desc item-desc-tr">
                            Marine edilmiş tavuk parçaları, sebzelerle ızgarada pişirilmiş.
                        </p>
                        <p class="item-desc item-desc-en" style="display: none;">
                            Marinated chicken pieces grilled with vegetables.
                        </p>
                        <p class="item-desc item-desc-ar" style="display: none;">
                            قطع دجاج مُتبلة مشوية مع الخضروات.
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <!-- İçecekler Bölümü -->
        <section class="menu-section" id="drinks" style="display: none;">
            <h2 class="section-title">
                <i class="fas fa-glass-martini-alt"></i>
                <span class="tr">İçecekler</span>
                <span class="en" style="display: none;">Drinks</span>
                <span class="ar" style="display: none;">مشروبات</span>
            </h2>
            <div class="menu-items">
                <!-- İçecek Öğe 1 -->
                <div class="menu-item slide-in-left">
                    <div class="item-image">
                        <a href="https://images.unsplash.com/photo-1544145345-1d3a15c14e40?ixlib=rb-1.2.1&auto=format&fit=crop&w=1000&q=80" class="image-zoom">
                            <img src="https://images.unsplash.com/photo-1544145345-1d3a15c14e40?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Türk Çayı">
                        </a>
                    </div>
                    <div class="item-content">
                        <h3 class="item-title">
                            <span class="tr">Türk Çayı</span>
                            <span class="en" style="display: none;">Turkish Tea</span>
                            <span class="ar" style="display: none;">شاي تركي</span>
                            <span class="item-price">₺9.99</span>
                        </h3>
                        <p class="item-desc item-desc-tr">
                            Taze demlenmiş geleneksel Türk çayı.
                        </p>
                        <p class="item-desc item-desc-en" style="display: none;">
                            Freshly brewed traditional Turkish tea.
                        </p>
                        <p class="item-desc item-desc-ar" style="display: none;">
                            شاي تركي تقليدي طازج المخمر.
                        </p>
                    </div>
                </div>

                <!-- İçecek Öğe 2 -->
                <div class="menu-item slide-in-right">
                    <div class="item-image">
                        <a href="https://images.unsplash.com/photo-1512568400610-3f3f518baa39?ixlib=rb-1.2.1&auto=format&fit=crop&w=1000&q=80" class="image-zoom">
                            <img src="https://images.unsplash.com/photo-1512568400610-3f3f518baa39?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Türk Kahvesi">
                        </a>
                    </div>
                    <div class="item-content">
                        <h3 class="item-title">
                            <span class="tr">Türk Kahvesi</span>
                            <span class="en" style="display: none;">Turkish Coffee</span>
                            <span class="ar" style="display: none;">قهوة تركية</span>
                            <span class="item-price">₺19.99</span>
                        </h3>
                        <p class="item-desc item-desc-tr">
                            Köpüklü ve yoğun kıvamlı otantik Türk kahvesi.
                        </p>
                        <p class="item-desc item-desc-en" style="display: none;">
                            Foamy and thick authentic Turkish coffee.
                        </p>
                        <p class="item-desc item-desc-ar" style="display: none;">
                            قهوة تركية أصيلة رغوية وكثيفة القوام.
                        </p>
                    </div>
                </div>

                <!-- İçecek Öğe 3 -->
                <div class="menu-item slide-in-left">
                    <div class="item-image">
                        <a href="https://images.unsplash.com/photo-1627806055486-6da24d5c3799?ixlib=rb-1.2.1&auto=format&fit=crop&w=1000&q=80" class="image-zoom">
                            <img src="https://images.unsplash.com/photo-1627806055486-6da24d5c3799?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=80" alt="Ayran">
                        </a>
                    </div>
                    <div class="item-content">
                        <h3 class="item-title">
                            <span class="tr">Ayran</span>
                            <span class="en" style="display: none;">Ayran</span>
                            <span class="ar" style="display: none;">أيران</span>
                            <span class="item-price">₺14.99</span>
                        </h3>
                        <p class="item-desc item-desc-tr">
                            Serinletici yoğurt bazlı geleneksel içecek.
                        </p>
                        <p class="item-desc item-desc-en" style="display: none;">
                            Refreshing yogurt-based traditional drink.
                        </p>
                        <p class="item-desc item-desc-ar" style="display: none;">
                            مشروب تقليدي منعش قائم على الزبادي.
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Hakkımızda Bölümü -->
        <div class="about-section">
            <h2 class="tr">Hakkımızda</h2>
            <h2 class="en" style="display: none;">About Us</h2>
            <h2 class="ar" style="display: none;">من نحن</h2>
            <p class="tr">Lezzet Durağı, 2010 yılından bu yana geleneksel ve modern tatları bir araya getirerek misafirlerine unutulmaz bir deneyim sunmaktadır. Tüm malzemelerimiz günlük ve tazedir.</p>
            <p class="en" style="display: none;">Flavor Stop has been bringing together traditional and modern flavors since 2010, offering an unforgettable experience to its guests. All our ingredients are daily and fresh.</p>
            <p class="ar" style="display: none;">تقدم محطة النكهات منذ عام 2010 تجربة لا تُنسى لضيوفها من خلال الجمع بين النكهات التقليدية والحديثة. جميع مكوناتنا طازجة ويومية.</p>
            <p class="tr">Usta şeflerimizin özenle hazırladığı yemeklerimiz ve sıcak personelimizle sizleri ağırlamaktan mutluluk duyuyoruz.</p>
            <p class="en" style="display: none;">We are happy to host you with our meals carefully prepared by our master chefs and our warm staff.</p>
            <p class="ar" style="display: none;">يسعدنا استضافتكم مع وجباتنا المعدة بعناية من قبل طهاة خبراء وطاقمنا الودود.</p>
        </div>
    </main>

    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/magnific-popup.js/1.1.0/jquery.magnific-popup.min.js"></script>
    <script>
        // Dil değiştirme fonksiyonu
        function changeLanguage(lang) {
            document.documentElement.lang = lang;
            
            // Aktif bayrağı güncelle
            document.querySelectorAll('.lang-flag').forEach(flag => {
                flag.classList.remove('active');
            });
            event.target.classList.add('active');
            
            // Dil içeriğini değiştir
            document.querySelectorAll('.tr, .en, .ar').forEach(el => {
                el.style.display = 'none';
            });
            document.querySelectorAll(`.${lang}`).forEach(el => {
                el.style.display = (el.tagName === 'SPAN' || el.tagName === 'P' || el.tagName === 'STRONG' || el.tagName === 'H2') ? 'inline' : 'block';
            });

            document.body.style.direction = (lang === 'ar') ? 'rtl' : 'ltr';
        }

        // Duyurular butonu toggle
        document.querySelector('.announcement-btn').addEventListener('click', function() {
            const box = document.querySelector('.announcement-box');
            box.style.display = (box.style.display === 'block') ? 'none' : 'block';
        });

        // Kategori navigasyonu
        document.querySelectorAll('.category-btn').forEach(btn => {
            btn.addEventListener('click', function() {
                // Aktif butonu güncelle
                document.querySelectorAll('.category-btn').forEach(btn => {
                    btn.classList.remove('active');
                });
                this.classList.add('active');
                
                // Seçilen kategoriyi göster
                const category = this.getAttribute('data-category');
                document.querySelectorAll('.menu-section').forEach(section => {
                    section.style.display = 'none';
                });
                document.getElementById(category).style.display = 'block';
                
                // Öğeleri animasyonla göster
                const items = document.querySelectorAll(`#${category} .menu-item`);
                items.forEach((item, index) => {
                    item.style.opacity = '0';
                    setTimeout(() => {
                        item.classList.remove('slide-in-left', 'slide-in-right');
                        item.classList.add(index % 2 === 0 ? 'slide-in-left' : 'slide-in-right');
                        item.style.opacity = '1';
                    }, 10);
                });
            });
        });

        // Resim büyütme
        $(document).ready(function() {
            $('.image-zoom').magnificPopup({
                type: 'image',
                closeOnContentClick: true,
                mainClass: 'mfp-img-mobile',
                image: {
                    verticalFit: true
                },
                zoom: {
                    enabled: true,
                    duration: 300,
                    easing: 'ease-in-out'
                }
            });
        });

        // Sayfa yüklendiğinde animasyonları başlat
        window.addEventListener('load', function() {
            const items = document.querySelectorAll('.menu-item');
            items.forEach((item, index) => {
                setTimeout(() => {
                    item.style.opacity = '1';
                }, index * 150);
            });
        });
    </script>
    <script>

</body>
</html>
