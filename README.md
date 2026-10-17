```html
<!DOCTYPE html>
<html lang="ar" dir="rtl" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VELORA | Eau De Parfum — الإطلالة الرسمية للعطر</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Cinzel for VELORA Luxury Serif & Tajawal for Modern Arabic -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;500;600;700&family=Playfair+Display:ital,wght@0,400;0,600;1,400&family=Tajawal:wght@300;400;500;700;800&display=swap" rel="stylesheet">
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <!-- Three.js 3D WebGL Engine -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        obsidian: '#060606',
                        charcoal: '#111111',
                        gold: {
                            light: '#f3e5ab',
                            DEFAULT: '#d4af37',
                            warm: '#c59b27',
                            dark: '#8a6d1b'
                        },
                        amber: {
                            glow: '#b87333',
                            deep: '#4a2c11'
                        }
                    },
                    fontFamily: {
                        arabic: ['Tajawal', 'sans-serif'],
                        luxury: ['Cinzel', 'serif'],
                        editorial: ['Playfair Display', 'serif']
                    }
                }
            }
        }
    </script>

    <style>
        :root {
            --ambient-color: rgba(212, 175, 55, 0.16);
            --accent-gold: #d4af37;
        }

        body {
            background-color: #060606;
            color: #f5f5f4;
            font-family: 'Tajawal', sans-serif;
            overflow-x: hidden;
            selection-background-color: #d4af37;
            selection-color: #060606;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #060606;
        }
        ::-webkit-scrollbar-thumb {
            background: linear-gradient(to bottom, #8a6d1b, #d4af37);
            border-radius: 9999px;
        }

        /* Luxury Gold Gradient Text */
        .gold-gradient-text {
            background: linear-gradient(135deg, #fff6d6 0%, #d4af37 45%, #9a7432 80%, #f3e5ab 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-size: 200% auto;
            animation: shineText 6s linear infinite;
        }

        @keyframes shineText {
            to {
                background-position: 200% center;
            }
        }

        /* 3D Perspective Stage */
        .perspective-stage {
            perspective: 1400px;
        }
        .tilt-card {
            transform-style: preserve-3d;
            transition: transform 0.18s cubic-bezier(0.2, 0.8, 0.2, 1), box-shadow 0.3s ease;
            will-change: transform;
        }
        .tilt-depth-layer {
            transform: translateZ(45px);
        }

        /* Pulsing Hotspots */
        .hotspot-pin {
            position: absolute;
            width: 34px;
            height: 34px;
            margin-left: -17px;
            margin-top: -17px;
            border-radius: 9999px;
            background: rgba(10, 10, 10, 0.85);
            border: 1.5px solid #d4af37;
            color: #f3e5ab;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 30;
            transition: all 0.3s ease;
            box-shadow: 0 0 20px rgba(212, 175, 55, 0.5);
        }
        .hotspot-pin::before {
            content: '';
            position: absolute;
            inset: -7px;
            border-radius: 9999px;
            border: 1px solid rgba(212, 175, 55, 0.65);
            animation: pulseRing 2.2s cubic-bezier(0.24, 0, 0.38, 1) infinite;
        }
        .hotspot-pin:hover, .hotspot-pin.active {
            transform: scale(1.22);
            background: #d4af37;
            color: #060606;
            box-shadow: 0 0 30px rgba(212, 175, 55, 0.95);
        }

        @keyframes pulseRing {
            0% { transform: scale(0.8); opacity: 0.9; }
            100% { transform: scale(1.7); opacity: 0; }
        }

        /* Smart Grid Slicer Styles for 3x3 (1000088394.png) and 3x2 (1000088395.png) */
        .sliced-photo-3x3 {
            background-repeat: no-repeat;
            /* 306% crops out the white grid separator lines cleanly */
            background-size: 306% 306%;
            transition: transform 0.65s cubic-bezier(0.16, 1, 0.3, 1), filter 0.5s ease;
        }
        .sliced-photo-3x2 {
            background-repeat: no-repeat;
            /* 306% width x 205% height crops out the white separator lines on the 3x2 grid */
            background-size: 306% 205%;
            transition: transform 0.65s cubic-bezier(0.16, 1, 0.3, 1), filter 0.5s ease;
        }
        .gallery-card:hover .sliced-photo-3x3,
        .gallery-card:hover .sliced-photo-3x2 {
            transform: scale(1.06);
        }

        /* Magnifying Glass Loupe */
        .loupe-lens {
            position: absolute;
            width: 155px;
            height: 155px;
            border-radius: 50%;
            border: 2px solid #d4af37;
            box-shadow: 0 15px 40px rgba(0,0,0,0.85), inset 0 0 20px rgba(212,175,55,0.35);
            pointer-events: none;
            opacity: 0;
            transform: translate(-50%, -50%) scale(0.75);
            transition: opacity 0.2s ease, transform 0.2s ease;
            z-index: 40;
            background-repeat: no-repeat;
        }
        .gallery-card.loupe-enabled:hover .loupe-lens {
            opacity: 1;
            transform: translate(-50%, -50%) scale(1);
        }

        /* Glassmorphism Panels */
        .luxury-glass {
            background: rgba(17, 17, 17, 0.72);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(212, 175, 55, 0.22);
        }

        /* Ambient Background Glow */
        .ambient-orb {
            background: radial-gradient(circle, var(--ambient-color) 0%, rgba(6,6,6,0) 70%);
            transition: background 0.8s ease;
        }
    </style>
</head>
<body class="relative min-h-screen selection:bg-gold selection:text-obsidian">

    <!-- Full-Screen Interactive Mist & Particles Canvas -->
    <canvas id="aromaCanvas" class="fixed inset-0 pointer-events-none z-40"></canvas>

    <!-- Top Interactive Image Sync Bar (Allows instant drag/upload of the 3 images if not in same folder) -->
    <div id="syncBanner" class="relative z-50 bg-gradient-to-r from-obsidian via-[#17130a] to-obsidian border-b border-gold/30 px-4 py-2.5">
        <div class="max-w-7xl mx-auto flex flex-wrap items-center justify-between gap-3 text-xs sm:text-sm">
            <div class="flex items-center gap-2.5">
                <span class="inline-flex items-center justify-center w-6 h-6 rounded-full bg-gold/20 text-gold border border-gold/40">
                    <i class="fa-solid fa-wand-magic-sparkles text-xs"></i>
                </span>
                <p class="text-stone-300">
                    <span class="text-gold font-semibold">محرك الصور التفاعلي الذكي:</span>
                    يقرأ تلقائياً الصور (<code class="text-gold-light">1000088393.png</code> و <code class="text-gold-light">1000088394.png</code> و <code class="text-gold-light">1000088395.png</code>) ويقسم الشبكات إلى 15 لقطة تفاعلية.
                </p>
            </div>
            <div class="flex items-center gap-2">
                <label for="multiImageInput" class="cursor-pointer inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-gold text-obsidian font-bold hover:bg-gold-light transition shadow-lg shadow-gold/20 text-xs">
                    <i class="fa-solid fa-images"></i>
                    <span>إدراج صور العطر الـ 3 للمعاينة الحية</span>
                </label>
                <input id="multiImageInput" type="file" accept="image/*" multiple class="hidden">
                <button onclick="openImageManagerModal()" class="px-3 py-1.5 rounded-full border border-gold/40 text-gold-light hover:bg-gold/10 transition text-xs">
                    تخصيص كل صورة
                </button>
            </div>
        </div>
    </div>

    <!-- Luxury Sticky Navigation -->
    <header class="sticky top-0 z-40 luxury-glass border-b border-white/5">
        <div class="max-w-7xl mx-auto px-4 sm:px-8 h-20 flex items-center justify-between">
            <!-- Right: Arabic Brand Tag -->
            <div class="flex items-center gap-4">
                <a href="#hero" class="group flex items-center gap-3">
                    <div class="w-10 h-10 rounded-lg bg-gradient-to-br from-stone-900 to-black border border-gold/50 flex items-center justify-center shadow-inner">
                        <span class="font-luxury text-xl font-bold gold-gradient-text tracking-widest">V</span>
                    </div>
                    <div class="hidden sm:block">
                        <span class="block font-luxury text-lg tracking-[0.28em] text-white">VELORA</span>
                        <span class="block text-[10px] tracking-[0.22em] text-gold/80 uppercase">Eau De Parfum</span>
                    </div>
                </a>
            </div>

            <!-- Center: Navigation Links -->
            <nav class="hidden md:flex items-center gap-7 text-sm font-medium text-stone-300">
                <a href="#hero" class="hover:text-gold transition">الرئيسية</a>
                <a href="#studio3d" class="text-gold font-bold flex items-center gap-1.5 bg-gold/10 px-3 py-1.5 rounded-full border border-gold/40 hover:bg-gold hover:text-obsidian transition">
                    <i class="fa-solid fa-cube"></i>
                    <span>المجسم 3D التفاعلي 360°</span>
                </a>
                <a href="#anatomy" class="hover:text-gold transition">تشريح الزجاجة</a>
                <a href="#olfactory" class="hover:text-gold transition">الهرم العطري</a>
                <a href="#gallery" class="hover:text-gold transition">المعرض (15 لقطة)</a>
                <a href="#script-modal" onclick="toggleCodeModal(true); return false;" class="text-gold-light flex items-center gap-1.5 hover:underline">
                    <i class="fa-solid fa-code text-xs"></i>
                    <span>السكربت</span>
                </a>
            </nav>

            <!-- Left: Interactive Spray Experience Trigger & Audio Toggle -->
            <div class="flex items-center gap-3">
                <button onclick="triggerPerfumeSpray()" class="relative overflow-hidden group px-4 py-2 rounded-full bg-gradient-to-r from-gold-dark via-gold to-gold-warm text-obsidian font-bold text-xs sm:text-sm shadow-lg shadow-gold/20 hover:shadow-gold/40 transition flex items-center gap-2">
                    <i class="fa-solid fa-spray-can-sparkles transition-transform group-hover:rotate-12"></i>
                    <span>رَشّ العطر تفاعلياً</span>
                </button>
                <button id="soundToggleBtn" onclick="toggleAudio()" title="تفعيل/كتم المؤثرات الصوتية للعطر" class="w-9 h-9 rounded-full border border-white/15 flex items-center justify-center text-stone-300 hover:text-gold hover:border-gold/50 transition">
                    <i id="soundIcon" class="fa-solid fa-volume-high text-xs"></i>
                </button>
            </div>
        </div>
    </header>

    <!-- ==========================================
         SECTION 1: HERO 3D INTERACTIVE SHOWCASE (1000088393.png)
         ========================================== -->
    <section id="hero" class="relative min-h-[90vh] flex items-center py-14 sm:py-20 overflow-hidden">
        <!-- Ambient Background Lighting -->
        <div class="ambient-orb absolute -top-32 -right-32 w-[550px] h-[550px] rounded-full pointer-events-none"></div>
        <div class="ambient-orb absolute bottom-0 -left-40 w-[600px] h-[600px] rounded-full pointer-events-none"></div>

        <div class="max-w-7xl mx-auto px-4 sm:px-8 w-full relative z-10">
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
                
                <!-- Right Column (Arabic Story & Interactive Controls) -->
                <div class="lg:col-span-5 space-y-6 text-right">
                    <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-white/5 border border-gold/30 text-gold-light text-xs tracking-wider">
                        <span class="w-2 h-2 rounded-full bg-gold animate-ping"></span>
                        <span>إصدار خاص • استعراض حصري للهوية</span>
                    </div>

                    <div class="space-y-2">
                        <p class="font-luxury text-xs sm:text-sm tracking-[0.35em] text-gold uppercase">
                            MORE THAN A FRAGRANCE, IT'S A PRESENCE
                        </p>
                        <h1 class="font-luxury text-5xl sm:text-7xl font-bold tracking-[0.18em] gold-gradient-text leading-tight">
                            VELORA
                        </h1>
                        <p class="text-xl sm:text-2xl font-light text-stone-200 mt-1">
                            أكثر من مجرّد عطر.. إنّهُ <span class="text-gold font-semibold">حضورٌ يفرضُ هيبته</span>
                        </p>
                    </div>

                    <p class="text-stone-400 leading-relaxed text-sm sm:text-base">
                        تحفة عطرية صُممت لتجسد التناقض الساحر بين غموض الرخام الأسود ودفء الكهرمان الذهبي. يمزج <strong class="text-white font-medium">VELORA Eau De Parfum</strong> بين نقاء الأزهار البيضاء، ونفحات البخور المدخن، وعمق أخشاب العود المعتقة في زجاجة هندسية محفورة بحرف <span class="font-luxury text-gold">V</span>.
                    </p>

                    <!-- Technical Specs Pills from Bottle -->
                    <div class="grid grid-cols-3 gap-3 pt-2">
                        <div class="luxury-glass p-3.5 rounded-xl text-center border border-white/10">
                            <span class="block text-[11px] text-stone-400">التركيز العطري</span>
                            <span class="font-luxury text-xs sm:text-sm font-bold text-gold-light mt-1 block">EAU DE PARFUM</span>
                        </div>
                        <div class="luxury-glass p-3.5 rounded-xl text-center border border-white/10">
                            <span class="block text-[11px] text-stone-400">الحجم الرسمي</span>
                            <span class="font-luxury text-xs sm:text-sm font-bold text-white mt-1 block">100 ML</span>
                        </div>
                        <div class="luxury-glass p-3.5 rounded-xl text-center border border-white/10">
                            <span class="block text-[11px] text-stone-400">الوزن السائل</span>
                            <span class="font-luxury text-xs sm:text-sm font-bold text-gold-light mt-1 block">3.4 FL.OZ.</span>
                        </div>
                    </div>

                    <!-- Active Hotspot Info Box (Updates dynamically when clicking pins on the image) -->
                    <div id="hotspotInfoPanel" class="luxury-glass rounded-2xl p-5 border-r-4 border-r-gold transition-all duration-300">
                        <div class="flex items-center justify-between mb-1.5">
                            <span id="hotspotBadge" class="text-xs font-bold text-gold tracking-wider uppercase">
                                <i class="fa-solid fa-hand-pointer ml-1"></i> نقطة تفاعلية 01 / 04
                            </span>
                            <span class="text-[11px] text-stone-400">اضغط على النقاط الذهبية فوق الصورة</span>
                        </div>
                        <h3 id="hotspotTitle" class="text-lg font-bold text-white">الغطاء الأسود المحفور بحرف (V)</h3>
                        <p id="hotspotDesc" class="text-sm text-stone-300 mt-1 leading-relaxed">
                            غطاء هندسي مربع بلون الأوبسيديان الأسود المطفي، يتوسط قمته شعار حرف V المحفور بدقة مع طوق ذهبي مصقول يعكس الفخامة.
                        </p>
                    </div>

                    <!-- Interactive Action Bar -->
                    <div class="flex flex-wrap items-center gap-3 pt-2">
                        <a href="#studio3d" class="px-6 py-3.5 rounded-xl bg-gold text-obsidian font-bold text-sm hover:bg-gold-light transition shadow-xl shadow-gold/20 flex items-center gap-2.5">
                            <i class="fa-solid fa-cubes"></i>
                            <span>تجربة المجسم ثلاثي الأبعاد 360°</span>
                        </a>
                        <button onclick="triggerPerfumeSpray()" class="px-5 py-3.5 rounded-xl border border-gold/40 text-gold-light hover:bg-gold/10 transition text-sm font-medium flex items-center gap-2">
                            <i class="fa-solid fa-wind"></i>
                            <span>إطلاق السحابة العطرية</span>
                        </button>
                    </div>
                </div>

                <!-- Left Column: Interactive 3D Tilt Stage with Image 1 (1000088393.png) & Hotspots -->
                <div class="lg:col-span-7 perspective-stage">
                    <div id="heroTiltCard" class="tilt-card relative rounded-3xl overflow-hidden border border-gold/30 shadow-[0_25px_75px_rgba(0,0,0,0.95)] bg-charcoal aspect-square max-w-[600px] mx-auto select-none">
                        
                        <!-- Dynamic Cursor Spotlight Overlay -->
                        <div id="heroSpotlight" class="absolute inset-0 pointer-events-none z-20 opacity-0 transition-opacity duration-300" style="background: radial-gradient(420px circle at 50% 50%, rgba(212, 175, 55, 0.22), transparent 70%);"></div>

                        <!-- Main Hero Image (1000088393.png) -->
                        <img id="heroMainImg" 
                             src="1000088393.png" 
                             alt="VELORA Eau De Parfum 100ML" 
                             class="w-full h-full object-cover transition-transform duration-700"
                             onerror="handleImageFallback(this, 'hero')">

                        <!-- Subtle Luxury Vignette -->
                        <div class="absolute inset-0 bg-gradient-to-t from-obsidian/80 via-transparent to-obsidian/20 pointer-events-none z-10"></div>

                        <!-- Interactive Hotspot 1: Cap ('V' Engraved) -->
                        <button class="hotspot-pin active" style="top: 26%; left: 66%;" onclick="selectHotspot(0, this)" aria-label="الغطاء الأسود">
                            <span class="text-xs font-bold">1</span>
                        </button>

                        <!-- Interactive Hotspot 2: Gold Atomizer Neck (Spray Trigger) -->
                        <button class="hotspot-pin" style="top: 35.5%; left: 66%;" onclick="selectHotspot(1, this); triggerPerfumeSpray();" aria-label="البخاخ الذهبي">
                            <i class="fa-solid fa-spray-can-sparkles text-xs"></i>
                        </button>

                        <!-- Interactive Hotspot 3: Gradient Amber Bottle Body -->
                        <button class="hotspot-pin" style="top: 58%; left: 65%;" onclick="selectHotspot(2, this)" aria-label="زجاج العطر الكهرماني">
                            <span class="text-xs font-bold">3</span>
                        </button>

                        <!-- Interactive Hotspot 4: Matte Black Luxury Box -->
                        <button class="hotspot-pin" style="top: 44%; left: 33%;" onclick="selectHotspot(3, this)" aria-label="العلبة الفاخرة">
                            <span class="text-xs font-bold">4</span>
                        </button>

                        <!-- Bottom Floating HUD inside 3D Card -->
                        <div class="absolute bottom-4 inset-x-4 z-30 flex items-center justify-between px-4 py-2.5 rounded-2xl bg-black/75 backdrop-blur-md border border-white/10 text-xs">
                            <div class="flex items-center gap-2 text-gold-light">
                                <i class="fa-solid fa-cube animate-pulse"></i>
                                <span>حرّك المؤشر لإمالة المنصة ثلاثية الأبعاد (3D Tilt)</span>
                            </div>
                            <button onclick="openLightbox('hero', 'الصورة الرسمية: الزجاجة والعلبة الفاخرة', 'VELORA EAU DE PARFUM — 100 ML e 3.4 FL.OZ.')" class="text-white hover:text-gold flex items-center gap-1.5 font-medium">
                                <i class="fa-solid fa-expand"></i>
                                <span>تكبير</span>
                            </button>
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- ==========================================
         SECTION 1.5: REAL-TIME 3D WEBGL PRODUCT STUDIO (360° THREE.JS)
         ========================================== -->
    <section id="studio3d" class="py-20 relative overflow-hidden border-t border-gold/25 bg-gradient-to-b from-[#070707] via-[#0e0b07] to-[#080808]">
        <div class="max-w-7xl mx-auto px-4 sm:px-8">
            
            <!-- Section Header -->
            <div class="flex flex-col lg:flex-row lg:items-end justify-between gap-6 mb-10">
                <div>
                    <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-gold/15 border border-gold/40 text-gold text-xs font-bold tracking-widest uppercase mb-3">
                        <i class="fa-solid fa-cube animate-spin" style="animation-duration: 8s;"></i>
                        <span>استوديو WebGL ثلاثي الأبعاد الحقيقي • 360°</span>
                    </div>
                    <h2 class="text-3xl sm:text-5xl font-bold text-white">
                        استعراض العطر والمنتجات <span class="font-luxury gold-gradient-text">3D</span>
                    </h2>
                    <p class="text-stone-400 text-sm sm:text-base mt-2 max-w-2xl">
                        تحكّم كامل بمجسم عطر <strong class="text-white">VELORA Eau De Parfum</strong> وعلبته الفاخرة وألواح العرض البلورية في بيئة ثلاثية الأبعاد. اسحب بالماوس أو بإصبعك للتدوير 360°، وافتح الغطاء لرؤية البخاخ الذهبي وتفكيك أجزاء الزجاجة.
                    </p>
                </div>

                <!-- Quick Studio Lighting Switcher -->
                <div class="flex flex-wrap items-center gap-2">
                    <span class="text-xs text-stone-400 ml-2">إضاءة الاستوديو:</span>
                    <button onclick="set3DLightingMood('gold', this)" class="studio-light-btn px-3.5 py-2 rounded-xl bg-gold text-obsidian font-bold text-xs transition">
                        كهرمان ذهبي
                    </button>
                    <button onclick="set3DLightingMood('obsidian', this)" class="studio-light-btn px-3.5 py-2 rounded-xl bg-white/5 text-stone-300 hover:bg-white/10 border border-white/10 text-xs transition">
                        رخام ليلي
                    </button>
                    <button onclick="set3DLightingMood('sunset', this)" class="studio-light-btn px-3.5 py-2 rounded-xl bg-white/5 text-stone-300 hover:bg-white/10 border border-white/10 text-xs transition">
                        غروب درامي
                    </button>
                </div>
            </div>

            <!-- Main 3D Stage Grid -->
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-stretch">
                
                <!-- Right Control Panel: Interactive 3D Actions -->
                <div class="lg:col-span-4 flex flex-col justify-between space-y-4">
                    
                    <div class="luxury-glass rounded-3xl p-6 border border-gold/30 space-y-5">
                        <div class="flex items-center justify-between border-b border-white/10 pb-3">
                            <h3 class="font-bold text-white text-lg flex items-center gap-2">
                                <i class="fa-solid fa-sliders text-gold"></i>
                                <span>لوحة التحكم بالمجسم 3D</span>
                            </h3>
                            <span id="studioStatusBadge" class="text-[11px] px-2.5 py-0.5 rounded-full bg-gold/20 text-gold border border-gold/30">
                                تفاعلي مباشر
                            </span>
                        </div>

                        <!-- 3D Action Buttons -->
                        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-1 gap-3">
                            
                            <!-- 1. Open / Close Cap -->
                            <button id="btnCapToggle" onclick="toggle3DCap()" class="w-full p-3.5 rounded-2xl bg-white/5 hover:bg-gold/15 border border-white/10 hover:border-gold/50 transition flex items-center justify-between group text-right">
                                <div class="flex items-center gap-3">
                                    <div class="w-10 h-10 rounded-xl bg-gold/15 border border-gold/40 flex items-center justify-center text-gold group-hover:scale-110 transition">
                                        <i class="fa-solid fa-arrows-up-down"></i>
                                    </div>
                                    <div>
                                        <span id="capToggleTitle" class="block text-sm font-bold text-white">فتح الغطاء الأسود (V)</span>
                                        <span class="block text-[11px] text-stone-400">كشف البخاخ الذهبي ثلاثي الأبعاد</span>
                                    </div>
                                </div>
                                <i class="fa-solid fa-chevron-left text-xs text-gold"></i>
                            </button>

                            <!-- 2. 3D Volumetric Spray -->
                            <button onclick="trigger3DSpray()" class="w-full p-3.5 rounded-2xl bg-gradient-to-r from-gold/25 to-amber-glow/20 hover:from-gold hover:to-gold-warm border border-gold/50 transition flex items-center justify-between group text-right">
                                <div class="flex items-center gap-3">
                                    <div class="w-10 h-10 rounded-xl bg-black/50 border border-gold/40 flex items-center justify-center text-gold-light group-hover:scale-110 transition">
                                        <i class="fa-solid fa-spray-can-sparkles"></i>
                                    </div>
                                    <div>
                                        <span class="block text-sm font-bold text-white group-hover:text-obsidian">رَشّ العطر في الفضاء 3D</span>
                                        <span class="block text-[11px] text-stone-300 group-hover:text-obsidian/80">محاكاة ضغط البخاخ وانتشار الرذاذ</span>
                                    </div>
                                </div>
                                <i class="fa-solid fa-wind text-xs text-gold group-hover:text-obsidian"></i>
                            </button>

                            <!-- 3. Exploded View (Deconstruct Bottle) -->
                            <button id="btnExplodeToggle" onclick="toggle3DExplodedView()" class="w-full p-3.5 rounded-2xl bg-white/5 hover:bg-gold/15 border border-white/10 hover:border-gold/50 transition flex items-center justify-between group text-right">
                                <div class="flex items-center gap-3">
                                    <div class="w-10 h-10 rounded-xl bg-gold/15 border border-gold/40 flex items-center justify-center text-gold group-hover:scale-110 transition">
                                        <i class="fa-solid fa-layer-group"></i>
                                    </div>
                                    <div>
                                        <span id="explodeToggleTitle" class="block text-sm font-bold text-white">العرض التفكيكي (Exploded 3D)</span>
                                        <span class="block text-[11px] text-stone-400">فصل طبقات الزجاجة والغطاء والقلب الكهرماني</span>
                                    </div>
                                </div>
                                <i class="fa-solid fa-chevron-left text-xs text-gold"></i>
                            </button>

                            <!-- 4. Switch 3D Product Lineup Mode -->
                            <button id="btnLineupToggle" onclick="cycle3DProductMode()" class="w-full p-3.5 rounded-2xl bg-white/5 hover:bg-gold/15 border border-white/10 hover:border-gold/50 transition flex items-center justify-between group text-right">
                                <div class="flex items-center gap-3">
                                    <div class="w-10 h-10 rounded-xl bg-gold/15 border border-gold/40 flex items-center justify-center text-gold group-hover:scale-110 transition">
                                        <i class="fa-solid fa-boxes-stacked"></i>
                                    </div>
                                    <div>
                                        <span id="lineupToggleTitle" class="block text-sm font-bold text-white">المجموعة الكاملة (الزجاجة + العلبة + البخاخ)</span>
                                        <span class="block text-[11px] text-stone-400">تبديل عرض المنتجات ثلاثية الأبعاد على المنصة</span>
                                    </div>
                                </div>
                                <i class="fa-solid fa-repeat text-xs text-gold"></i>
                            </button>

                        </div>

                        <!-- Camera Preset Angles -->
                        <div class="pt-3 border-t border-white/10">
                            <span class="block text-xs text-stone-400 mb-2.5">زوايا الكاميرا السينمائية:</span>
                            <div class="grid grid-cols-4 gap-2 text-xs">
                                <button onclick="set3DCameraPreset('front')" class="py-2 rounded-xl bg-white/5 hover:bg-gold hover:text-obsidian border border-white/10 transition font-medium">الأمامية</button>
                                <button onclick="set3DCameraPreset('topV')" class="py-2 rounded-xl bg-white/5 hover:bg-gold hover:text-obsidian border border-white/10 transition font-medium">ختم V</button>
                                <button onclick="set3DCameraPreset('side')" class="py-2 rounded-xl bg-white/5 hover:bg-gold hover:text-obsidian border border-white/10 transition font-medium">الجانبية</button>
                                <button onclick="set3DCameraPreset('macro')" class="py-2 rounded-xl bg-white/5 hover:bg-gold hover:text-obsidian border border-white/10 transition font-medium">الماكرو</button>
                            </div>
                        </div>
                    </div>

                    <!-- Active 3D Part Inspector Info -->
                    <div class="luxury-glass rounded-2xl p-5 border-r-4 border-r-gold">
                        <div class="flex items-center justify-between text-xs text-gold mb-1">
                            <span class="font-bold"><i class="fa-solid fa-microscope ml-1"></i> مواصفات المجسم 3D</span>
                            <span class="font-luxury">PBR CRYSTAL & GOLD</span>
                        </div>
                        <p id="studio3DInfoText" class="text-xs sm:text-sm text-stone-300 leading-relaxed">
                            مجسم ثلاثي الأبعاد يحاكي زجاج <strong class="text-white">VELORA</strong> الكهرماني المتدرج مع انكسار الضوء الداخلي، طوق البخاخ الذهبي، والعلبة السوداء المطرزة بالذهب.
                        </p>
                    </div>

                </div>

                <!-- Left 3D WebGL Canvas Viewport -->
                <div class="lg:col-span-8 relative min-h-[500px] sm:min-h-[600px] rounded-3xl overflow-hidden border border-gold/40 bg-gradient-to-b from-[#13100c] via-[#090909] to-[#040404] shadow-[0_25px_80px_rgba(0,0,0,0.95)] flex flex-col">
                    
                    <!-- Top Floating Bar inside 3D Viewport -->
                    <div class="absolute top-4 inset-x-4 z-20 flex flex-wrap items-center justify-between gap-2 pointer-events-none">
                        <div class="px-3.5 py-1.5 rounded-full bg-black/70 backdrop-blur-md border border-white/10 text-xs text-stone-300 flex items-center gap-2">
                            <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span>
                            <span>اسحب للتدوير 360° • عجلة الماوس للتقريب</span>
                        </div>
                        <button onclick="toggle3DAutoRotate()" id="btnAutoRotate" class="pointer-events-auto px-3.5 py-1.5 rounded-full bg-gold/20 border border-gold/50 text-gold-light hover:bg-gold hover:text-obsidian transition text-xs font-bold flex items-center gap-1.5">
                            <i class="fa-solid fa-rotate"></i>
                            <span id="autoRotateText">الدوران التلقائي: مفعل</span>
                        </button>
                    </div>

                    <!-- Three.js Canvas Mount Container -->
                    <div id="velora3DContainer" class="w-full h-full flex-1 cursor-grab active:cursor-grabbing relative"></div>

                    <!-- Bottom Floating Labels inside 3D Viewport -->
                    <div class="absolute bottom-4 inset-x-4 z-20 flex flex-wrap items-center justify-between gap-3 px-4 py-3 rounded-2xl bg-black/75 backdrop-blur-md border border-white/10 text-xs">
                        <div class="flex items-center gap-4">
                            <div>
                                <span class="text-stone-400 block text-[10px]">المجسم المعروض</span>
                                <span id="current3DModelLabel" class="font-luxury text-gold-light font-bold">VELORA 100ML + LUXURY BOX + TRAVEL ATOMIZER</span>
                            </div>
                        </div>
                        <div class="flex items-center gap-2">
                            <button onclick="reset3DCamera()" class="px-3 py-1.5 rounded-lg bg-white/10 hover:bg-white/20 text-white transition">
                                <i class="fa-solid fa-compress ml-1"></i> إعادة ضبط الزاوية
                            </button>
                        </div>
                    </div>

                </div>

            </div>
        </div>
    </section>

    <!-- ==========================================
         SECTION 2: MACRO ANATOMY STRIP (Extracted directly from the 3x3 & 3x2 grids)
         ========================================== -->
    <section id="anatomy" class="py-16 border-y border-white/5 bg-[#090909] relative">
        <div class="max-w-7xl mx-auto px-4 sm:px-8">
            <div class="flex flex-col md:flex-row md:items-end justify-between mb-12 gap-4">
                <div>
                    <span class="text-gold text-xs font-bold tracking-widest uppercase block mb-2">تفاصيل مصوّرة من زوايا الماكرو</span>
                    <h2 class="text-3xl sm:text-4xl font-bold text-white">تشريح الفخامة في <span class="font-luxury text-gold">VELORA</span></h2>
                </div>
                <p class="text-stone-400 text-sm max-w-md">
                    تم استخلاص هذه اللقطات التفصيلية مباشرةً من شبكات صور العطر لإبراز حرفية التصميم من القمة المحفورة وحتى القاعدة الكهرمانية.
                </p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
                <!-- Macro 1: The 'V' Cap (From 1000088394.png Top-Right 100% 0%) -->
                <div onclick="openSlicedLightbox('grid9', '100% 0%', 'حفر شعار V على الغطاء الأسود', 'لقطة ماكرو تبرز الحفر الهندسي الدقيق لحرف V أعلى الغطاء الأسود مع الطوق الذهبي.')" class="group cursor-pointer luxury-glass rounded-2xl overflow-hidden border border-white/10 hover:border-gold/50 transition">
                    <div class="aspect-square overflow-hidden relative">
                        <div class="sliced-photo-3x3 w-full h-full" data-grid="grid9" style="background-position: 100% 0%;"></div>
                        <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent"></div>
                        <span class="absolute top-3 right-3 px-2.5 py-1 rounded-full bg-black/70 border border-gold/30 text-[11px] text-gold">01 • القمة</span>
                    </div>
                    <div class="p-4">
                        <h3 class="font-bold text-white group-hover:text-gold transition">ختم حرف V المحفور</h3>
                        <p class="text-xs text-stone-400 mt-1">غطاء أسود مطفي يتوجه شعار العلامة المحفور بدقة عالية.</p>
                    </div>
                </div>

                <!-- Macro 2: The Mist & Gold Atomizer (From 1000088395.png Bottom-Left 0% 100%) -->
                <div onclick="openSlicedLightbox('grid6', '0% 100%', 'البخاخ الذهبي وسحابة البخور', 'تصميم البخاخ المعدني الذهبي الذي يطلق رذاذاً ناعماً كثيفاً يملأ المكان بالحضور.')" class="group cursor-pointer luxury-glass rounded-2xl overflow-hidden border border-white/10 hover:border-gold/50 transition">
                    <div class="aspect-square overflow-hidden relative">
                        <div class="sliced-photo-3x2 w-full h-full" data-grid="grid6" style="background-position: 0% 100%;"></div>
                        <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent"></div>
                        <span class="absolute top-3 right-3 px-2.5 py-1 rounded-full bg-black/70 border border-gold/30 text-[11px] text-gold">02 • البخاخ</span>
                    </div>
                    <div class="p-4">
                        <h3 class="font-bold text-white group-hover:text-gold transition">فوهة الرذاذ الذهبية</h3>
                        <p class="text-xs text-stone-400 mt-1">توزيع ضبابي متجانس يطلق عبير العطر بنعومة فائقة.</p>
                    </div>
                </div>

                <!-- Macro 3: Fresh Dew Drops (From 1000088395.png Bottom-Right 100% 100%) -->
                <div onclick="openSlicedLightbox('grid6', '100% 100%', 'قطرات الندى والانتعاش الأول', 'تباين قطرات الماء النقية فوق السطح الأسود المطفي والزجاج الدافئ.')" class="group cursor-pointer luxury-glass rounded-2xl overflow-hidden border border-white/10 hover:border-gold/50 transition">
                    <div class="aspect-square overflow-hidden relative">
                        <div class="sliced-photo-3x2 w-full h-full" data-grid="grid6" style="background-position: 100% 100%;"></div>
                        <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent"></div>
                        <span class="absolute top-3 right-3 px-2.5 py-1 rounded-full bg-black/70 border border-gold/30 text-[11px] text-gold">03 • الملمس</span>
                    </div>
                    <div class="p-4">
                        <h3 class="font-bold text-white group-hover:text-gold transition">تباين الندى والأوبسيديان</h3>
                        <p class="text-xs text-stone-400 mt-1">مقاومة فائقة ولمسة بصرية تجمع بين البرودة والدفء.</p>
                    </div>
                </div>

                <!-- Macro 4: Liquid Amber Glow (From 1000088394.png Bottom-Center 50% 100%) -->
                <div onclick="openSlicedLightbox('grid9', '50% 100%', 'توهج الكهرمان السائل', 'قاعدة الزجاج السميكة التي تحتضن السائل العطري بلون العنبر والذهب.')" class="group cursor-pointer luxury-glass rounded-2xl overflow-hidden border border-white/10 hover:border-gold/50 transition">
                    <div class="aspect-square overflow-hidden relative">
                        <div class="sliced-photo-3x3 w-full h-full" data-grid="grid9" style="background-position: 50% 100%;"></div>
                        <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent"></div>
                        <span class="absolute top-3 right-3 px-2.5 py-1 rounded-full bg-black/70 border border-gold/30 text-[11px] text-gold">04 • القاعدة</span>
                    </div>
                    <div class="p-4">
                        <h3 class="font-bold text-white group-hover:text-gold transition">عمق الزجاج الكهرماني</h3>
                        <p class="text-xs text-stone-400 mt-1">تدرج لوني يحمي السائل العطري من الضوء ويبرز لمعان الذهب.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ==========================================
         SECTION 3: INTERACTIVE OLFACTORY PYRAMID & MOOD SWITCHER
         ========================================== -->
    <section id="olfactory" class="py-20 relative overflow-hidden">
        <div class="max-w-7xl mx-auto px-4 sm:px-8">
            <div class="text-center max-w-2xl mx-auto mb-14">
                <span class="text-gold text-xs font-bold tracking-widest uppercase">تفاعل حسي وبصري</span>
                <h2 class="text-3xl sm:text-5xl font-bold text-white mt-2">الهرم العطري التفاعلي</h2>
                <p class="text-stone-400 text-sm sm:text-base mt-3">
                    اضغط على كل طبقة عطرية لتغيير الإضاءة المحيطة واستعراض اللقطة الفوتوغرافية التي تجسّد مكوناتها داخل الموقع.
                </p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-12 gap-10 items-center">
                <!-- Right: Interactive Pyramid Steps -->
                <div class="lg:col-span-6 space-y-4">
                    <!-- Top Note -->
                    <button onclick="selectOlfactoryNote(0)" id="noteBtn0" class="olfactory-btn w-full text-right p-6 rounded-2xl luxury-glass border-2 border-gold transition-all flex items-start gap-4">
                        <div class="w-12 h-12 rounded-xl bg-gold/20 border border-gold flex items-center justify-center text-gold shrink-0 text-xl">
                            <i class="fa-solid fa-droplet"></i>
                        </div>
                        <div class="flex-1">
                            <div class="flex items-center justify-between">
                                <span class="text-xs font-bold text-gold uppercase tracking-wider">النفحات العليا • الانطباع الأول</span>
                                <span class="text-xs text-stone-400">0 - 15 دقيقة</span>
                            </div>
                            <h3 class="text-xl font-bold text-white mt-1">قطرات الندى الباردة، البرغموت الأسود، والهيل</h3>
                            <p class="text-sm text-stone-300 mt-1.5 leading-relaxed">
                                افتتاحية منعشة ومهيبة تحاكي قطرات المطر النقية على الصخور البركانية الداكنة، تمنحك شعوراً باليقظة والفخامة الفورية.
                            </p>
                        </div>
                    </button>

                    <!-- Heart Note -->
                    <button onclick="selectOlfactoryNote(1)" id="noteBtn1" class="olfactory-btn w-full text-right p-6 rounded-2xl luxury-glass border border-white/10 hover:border-gold/40 transition-all flex items-start gap-4">
                        <div class="w-12 h-12 rounded-xl bg-white/5 border border-white/15 flex items-center justify-center text-gold-light shrink-0 text-xl">
                            <i class="fa-solid fa-spa"></i>
                        </div>
                        <div class="flex-1">
                            <div class="flex items-center justify-between">
                                <span class="text-xs font-bold text-gold-light uppercase tracking-wider">قلب العطر • الهوية النابضة</span>
                                <span class="text-xs text-stone-400">15 دقيقة - 4 ساعات</span>
                            </div>
                            <h3 class="text-xl font-bold text-white mt-1">الياسمين الأبيض الليلي، حبوب القهوة المحمصة، والبخور</h3>
                            <p class="text-sm text-stone-300 mt-1.5 leading-relaxed">
                                تناغم ساحر بين رقة الزهور البيضاء ودفء التوابل المحمصة مع خيوط الدخان العطري التي تمنح العطر غموضه الجذاب.
                            </p>
                        </div>
                    </button>

                    <!-- Base Note -->
                    <button onclick="selectOlfactoryNote(2)" id="noteBtn2" class="olfactory-btn w-full text-right p-6 rounded-2xl luxury-glass border border-white/10 hover:border-gold/40 transition-all flex items-start gap-4">
                        <div class="w-12 h-12 rounded-xl bg-white/5 border border-white/15 flex items-center justify-center text-amber-glow shrink-0 text-xl">
                            <i class="fa-solid fa-fire-flame-simple"></i>
                        </div>
                        <div class="flex-1">
                            <div class="flex items-center justify-between">
                                <span class="text-xs font-bold text-amber-glow uppercase tracking-wider">قاعدة العطر • الثبات والحضور</span>
                                <span class="text-xs text-stone-400">أكثر من 12 ساعة</span>
                            </div>
                            <h3 class="text-xl font-bold text-white mt-1">أخشاب العود المعتقة، العنبر الدافئ، ولمسة الحرير</h3>
                            <p class="text-sm text-stone-300 mt-1.5 leading-relaxed">
                                قاعدة عميقة تدوم طويلاً، تستند على كسر العود الفاخر والعنبر الكهرماني لتترك أثراً لا يُنسى يترجم شعار <span class="font-luxury text-gold">It's a Presence</span>.
                            </p>
                        </div>
                    </button>
                </div>

                <!-- Left: Dynamic Visual Stage synced with the selected note -->
                <div class="lg:col-span-6">
                    <div class="relative rounded-3xl overflow-hidden border border-gold/40 shadow-2xl bg-charcoal aspect-square max-w-[520px] mx-auto">
                        <!-- Sliced Visual Display -->
                        <div id="olfactoryVisual" class="sliced-photo-3x2 w-full h-full transition-all duration-700" data-grid="grid6" style="background-position: 100% 100%;"></div>
                        
                        <div class="absolute inset-0 bg-gradient-to-t from-obsidian via-obsidian/20 to-transparent"></div>

                        <!-- Bottom Description Overlay -->
                        <div class="absolute bottom-6 inset-x-6 p-5 rounded-2xl luxury-glass border border-gold/30">
                            <div class="flex items-center justify-between mb-1">
                                <span id="olfactoryStageTag" class="text-xs text-gold font-bold">اللقطة المعبّرة: قطرات الندى على الغطاء</span>
                                <button onclick="triggerPerfumeSpray()" class="text-xs text-gold-light hover:underline flex items-center gap-1">
                                    <i class="fa-solid fa-spray-can-sparkles"></i>
                                    <span>محاكاة النفحة</span>
                                </button>
                            </div>
                            <p id="olfactoryStageQuote" class="text-sm text-stone-200">
                                "انتعاش يوقظ الحواس منذ اللحظة الأولى لملامسة العطر للبشرة."
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- ==========================================
         SECTION 4: SMART SLICED INTERACTIVE GALLERY (15 SHOTS FROM IMAGES 2 & 3)
         ========================================== -->
    <section id="gallery" class="py-20 bg-[#080808] border-t border-white/5">
        <div class="max-w-7xl mx-auto px-4 sm:px-8">
            
            <!-- Header & Controls -->
            <div class="flex flex-col lg:flex-row lg:items-end justify-between gap-6 mb-10">
                <div>
                    <div class="inline-flex items-center gap-2 text-gold text-xs font-bold tracking-widest uppercase mb-2">
                        <i class="fa-solid fa-table-cells-large"></i>
                        <span>تقطيع ذكي تلقائي للشبكات (9 + 6 لقطات)</span>
                    </div>
                    <h2 class="text-3xl sm:text-5xl font-bold text-white">المعرض التفاعلي الكامل</h2>
                    <p class="text-stone-400 text-sm mt-2 max-w-2xl">
                        قام السكربت بتحويل صورتي الشبكة المرفقة إلى <strong class="text-gold">15 لوحة فوتوغرافية مستقلة</strong> عالية الدقة. مرّر الماوس لاكتشاف التفاصيل أو فعّل <strong class="text-white">عدسة المجهر</strong> للتكبير الفوري.
                    </p>
                </div>

                <!-- Interactive Loupe Mode Switch -->
                <div class="flex flex-wrap items-center gap-3">
                    <button id="loupeToggleBtn" onclick="toggleLoupeMode()" class="px-4 py-2.5 rounded-xl border border-gold/50 bg-gold/10 text-gold-light hover:bg-gold hover:text-obsidian transition text-xs sm:text-sm font-bold flex items-center gap-2">
                        <i class="fa-solid fa-magnifying-glass-plus"></i>
                        <span id="loupeStatusText">عدسة المجهر التفاعلية: مفعّلة</span>
                    </button>
                </div>
            </div>

            <!-- Filter Tabs -->
            <div class="flex flex-wrap items-center gap-2 mb-10 pb-4 border-b border-white/10">
                <button onclick="filterGallery('all', this)" class="filter-tab active px-4 py-2 rounded-full bg-gold text-obsidian font-bold text-xs sm:text-sm transition">
                    الكل (15 لقطة)
                </button>
                <button onclick="filterGallery('nature', this)" class="filter-tab px-4 py-2 rounded-full bg-white/5 text-stone-300 hover:bg-white/10 text-xs sm:text-sm transition">
                    المكونات والطبيعة (5)
                </button>
                <button onclick="filterGallery('macro', this)" class="filter-tab px-4 py-2 rounded-full bg-white/5 text-stone-300 hover:bg-white/10 text-xs sm:text-sm transition">
                    تفاصيل الماكرو والرذاذ (4)
                </button>
                <button onclick="filterGallery('luxury', this)" class="filter-tab px-4 py-2 rounded-full bg-white/5 text-stone-300 hover:bg-white/10 text-xs sm:text-sm transition">
                    الفخامة والرخام والظلال (6)
                </button>
            </div>

            <!-- Dynamic 15-Card Grid Container (Populated by JavaScript Smart Slicer) -->
            <div id="slicedGalleryGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-7">
                <!-- Cards injected via JS -->
            </div>

        </div>
    </section>

    <!-- ==========================================
         SECTION 5: BRAND SIGNATURE BANNER
         ========================================== -->
    <section class="py-20 relative overflow-hidden border-t border-gold/20 bg-gradient-to-b from-obsidian to-[#0d0a06]">
        <div class="max-w-4xl mx-auto px-4 text-center space-y-6">
            <div class="w-16 h-16 rounded-2xl bg-gold/10 border border-gold/40 flex items-center justify-center mx-auto text-gold font-luxury text-3xl font-bold">
                V
            </div>
            <p class="font-luxury text-sm sm:text-base tracking-[0.4em] text-gold uppercase">
                MORE THAN A FRAGRANCE • IT'S A PRESENCE
            </p>
            <h2 class="text-3xl sm:text-5xl font-bold text-white leading-tight">
                صُمم ليكون توقيعك الشخصي الذي يسبق حضورك
            </h2>
            <p class="text-stone-400 max-w-xl mx-auto text-sm sm:text-base leading-relaxed">
                هذا الموقع مخصص للاستعراض البصري التفاعلي لهوية عطر <span class="text-white font-semibold">VELORA Eau De Parfum (100 ML)</span> وتفاصيله الفنية.
            </p>
            <div class="pt-4 flex flex-wrap justify-center gap-4">
                <button onclick="triggerPerfumeSpray()" class="px-7 py-3 rounded-full bg-gold text-obsidian font-bold text-sm hover:bg-gold-light transition shadow-lg shadow-gold/20">
                    تجربة السحابة العطرية مرة أخرى
                </button>
                <button onclick="toggleCodeModal(true)" class="px-7 py-3 rounded-full border border-gold/40 text-gold-light hover:bg-gold/10 transition text-sm">
                    عرض كود وسكربت تقسيم الصور التفاعلي
                </button>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="py-8 border-t border-white/10 text-center text-xs text-stone-500 bg-obsidian">
        <div class="max-w-7xl mx-auto px-4 flex flex-col sm:flex-row items-center justify-between gap-4">
            <p class="font-luxury tracking-[0.25em] text-stone-300">VELORA — EAU DE PARFUM • 100 ML e 3.4 FL.OZ.</p>
            <p>منصة استعراض بصرية تفاعلية خاصة بالعلامة التجارية — جميع الحقوق محفوظة © 2026</p>
        </div>
    </footer>

    <!-- ==========================================
         LIGHTBOX MODAL FOR FULL-SCREEN INSPECTION
         ========================================== -->
    <div id="lightboxModal" class="fixed inset-0 z-50 bg-black/95 backdrop-blur-xl hidden items-center justify-center p-4 sm:p-8">
        <button onclick="closeLightbox()" class="absolute top-6 left-6 w-12 h-12 rounded-full bg-white/10 hover:bg-gold hover:text-obsidian text-white flex items-center justify-center text-xl transition z-50">
            <i class="fa-solid fa-xmark"></i>
        </button>

        <div class="max-w-4xl w-full grid grid-cols-1 md:grid-cols-12 gap-6 items-center luxury-glass rounded-3xl p-4 sm:p-6 border border-gold/30">
            <div class="md:col-span-7 aspect-square rounded-2xl overflow-hidden bg-obsidian border border-white/10 relative">
                <div id="lightboxVisual" class="w-full h-full bg-no-repeat transition-transform duration-500 hover:scale-110 cursor-zoom-in"></div>
            </div>
            <div class="md:col-span-5 space-y-4 text-right p-2">
                <span class="inline-block px-3 py-1 rounded-full bg-gold/15 border border-gold/40 text-gold text-xs font-bold">
                    VELORA • استعراض عالي الدقة
                </span>
                <h3 id="lightboxTitle" class="text-2xl font-bold text-white"></h3>
                <p id="lightboxDesc" class="text-stone-300 text-sm leading-relaxed"></p>
                <div class="pt-4 border-t border-white/10 space-y-2 text-xs text-stone-400">
                    <div class="flex justify-between">
                        <span>العلامة التجارية:</span>
                        <span class="font-luxury text-white">VELORA</span>
                    </div>
                    <div class="flex justify-between">
                        <span>التركيز والحجم:</span>
                        <span class="font-luxury text-gold-light">EAU DE PARFUM — 100 ML</span>
                    </div>
                </div>
                <button onclick="triggerPerfumeSpray()" class="w-full py-3 rounded-xl bg-gold text-obsidian font-bold text-sm hover:bg-gold-light transition mt-4">
                    <i class="fa-solid fa-spray-can-sparkles ml-1"></i> إطلاق الرذاذ العطري مع هذه اللقطة
                </button>
            </div>
        </div>
    </div>

    <!-- ==========================================
         IMAGE MANAGER MODAL (Upload / Assign each of the 3 images)
         ========================================== -->
    <div id="imageManagerModal" class="fixed inset-0 z-50 bg-black/90 backdrop-blur-lg hidden items-center justify-center p-4">
        <div class="max-w-2xl w-full luxury-glass rounded-3xl p-6 sm:p-8 border border-gold/40 space-y-6">
            <div class="flex items-center justify-between border-b border-white/10 pb-4">
                <div>
                    <h3 class="text-xl font-bold text-white">إدارة وربط صور العطر الثلاث</h3>
                    <p class="text-xs text-stone-400 mt-1">يمكنك رفع الصور الثلاث مباشرة من جهازك ليتم تطبيقها وتقطيعها فوراً في الموقع</p>
                </div>
                <button onclick="closeImageManagerModal()" class="w-9 h-9 rounded-full bg-white/10 text-white hover:bg-gold hover:text-obsidian flex items-center justify-center">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                <!-- Slot 1 -->
                <div class="p-4 rounded-2xl bg-white/5 border border-white/10 text-center space-y-3">
                    <span class="text-xs font-bold text-gold block">1. الصورة الرئيسية (المفردة)</span>
                    <code class="text-[11px] text-stone-400 block">1000088393.png</code>
                    <label class="cursor-pointer block py-2.5 px-3 rounded-xl bg-gold/20 border border-gold/40 text-gold-light text-xs font-bold hover:bg-gold hover:text-obsidian transition">
                        <i class="fa-solid fa-upload ml-1"></i> اختر الصورة 1
                        <input type="file" accept="image/*" class="hidden" onchange="updateSpecificImage('hero', this)">
                    </label>
                </div>
                <!-- Slot 2 -->
                <div class="p-4 rounded-2xl bg-white/5 border border-white/10 text-center space-y-3">
                    <span class="text-xs font-bold text-gold block">2. شبكة الـ 9 لقطات (3×3)</span>
                    <code class="text-[11px] text-stone-400 block">1000088394.png</code>
                    <label class="cursor-pointer block py-2.5 px-3 rounded-xl bg-gold/20 border border-gold/40 text-gold-light text-xs font-bold hover:bg-gold hover:text-obsidian transition">
                        <i class="fa-solid fa-upload ml-1"></i> اختر الصورة 2
                        <input type="file" accept="image/*" class="hidden" onchange="updateSpecificImage('grid9', this)">
                    </label>
                </div>
                <!-- Slot 3 -->
                <div class="p-4 rounded-2xl bg-white/5 border border-white/10 text-center space-y-3">
                    <span class="text-xs font-bold text-gold block">3. شبكة الـ 6 لقطات (3×2)</span>
                    <code class="text-[11px] text-stone-400 block">1000088395.png</code>
                    <label class="cursor-pointer block py-2.5 px-3 rounded-xl bg-gold/20 border border-gold/40 text-gold-light text-xs font-bold hover:bg-gold hover:text-obsidian transition">
                        <i class="fa-solid fa-upload ml-1"></i> اختر الصورة 3
                        <input type="file" accept="image/*" class="hidden" onchange="updateSpecificImage('grid6', this)">
                    </label>
                </div>
            </div>

            <div class="p-4 rounded-2xl bg-gold/10 border border-gold/30 text-xs text-stone-200 leading-relaxed">
                <i class="fa-solid fa-circle-info text-gold ml-1"></i>
                <strong>ملاحظة:</strong> عند وضع ملف `index.html` في نفس المجلد مع صورك الثلاث بنفس أسمائها (`1000088393.png`, `1000088394.png`, `1000088395.png`)، سيعمل الموقع تلقائياً بدون الحاجة لرفعها يدوياً.
            </div>
        </div>
    </div>

    <!-- ==========================================
         STANDALONE SCRIPT & CODE GUIDE MODAL
         ========================================== -->
    <div id="codeModal" class="fixed inset-0 z-50 bg-black/90 backdrop-blur-lg hidden items-center justify-center p-4">
        <div class="max-w-3xl w-full luxury-glass rounded-3xl p-6 sm:p-8 border border-gold/40 space-y-4 max-h-[90vh] flex flex-col">
            <div class="flex items-center justify-between border-b border-white/10 pb-3">
                <div>
                    <h3 class="text-lg sm:text-xl font-bold text-white">سكربت تحويل الصور المجمعة إلى بطاقات تفاعلية</h3>
                    <p class="text-xs text-stone-400">جاهز للنسخ والاستخدام أو التشغيل المباشر</p>
                </div>
                <button onclick="toggleCodeModal(false)" class="w-9 h-9 rounded-full bg-white/10 text-white hover:bg-gold hover:text-obsidian flex items-center justify-center">
                    <i class="fa-solid fa-xmark"></i>
                </button>
            </div>

            <div class="overflow-y-auto space-y-3 text-xs text-stone-300 leading-relaxed pr-1">
                <p>يعتمد هذا الموقع على تقنية <strong>Smart CSS Sprite Slicing & 3D Tilt</strong> بحيث يأخذ الصورة رقم 2 (`1000088394.png`) ويقسمها برمجياً عبر الإحداثيات (`0%`, `50%`, `100%`) إلى 9 صور مستقلة مع إخفاء الخطوط البيضاء الفاصلة عبر تكبير النسبة إلى `306%`، وكذلك الصورة رقم 3 (`1000088395.png`) إلى 6 صور مستقلة.</p>
                <pre id="snippetBox" dir="ltr" class="p-4 rounded-2xl bg-black/90 border border-white/10 text-gold-light overflow-x-auto font-mono text-[11px] leading-relaxed">/* سكربت تقسيم شبكات صور العطر وتحويلها لعناصر تفاعلية */
const VELORA_IMAGES = {
  hero: '1000088393.png',  // الصورة الرئيسية
  grid9: '1000088394.png', // شبكة 3×3 (9 لقطات)
  grid6: '1000088395.png'  // شبكة 3×2 (6 لقطات)
};

// إحداثيات استخراج الـ 9 لقطات من الصورة الثانية بدون الخطوط البيضاء
const coords3x3 = [
  '0% 0%',   '50% 0%',   '100% 0%',
  '0% 50%',  '50% 50%',  '100% 50%',
  '0% 100%', '50% 100%', '100% 100%'
];

// إحداثيات استخراج الـ 6 لقطات من الصورة الثالثة
const coords3x2 = [
  '0% 0%',   '50% 0%',   '100% 0%',
  '0% 100%', '50% 100%', '100% 100%'
];</pre>
            </div>

            <div class="flex justify-end gap-3 pt-2 border-t border-white/10">
                <button onclick="copyScriptSnippet()" id="copyBtnText" class="px-5 py-2.5 rounded-xl bg-gold text-obsidian font-bold text-xs hover:bg-gold-light transition">
                    <i class="fa-solid fa-copy ml-1"></i> نسخ السكربت
                </button>
                <button onclick="toggleCodeModal(false)" class="px-5 py-2.5 rounded-xl bg-white/10 text-white text-xs">
                    إغلاق
                </button>
            </div>
        </div>
    </div>

    <!-- ==========================================
         JAVASCRIPT ENGINE: SMART SLICER, 3D TILT, LOUPE, MIST & FALLBACKS
         ========================================== -->
    <script>
        // 1. Image Sources State (Defaults to exact filenames uploaded by user)
        const imageSources = {
            hero: '1000088393.png',
            grid9: '1000088394.png',
            grid6: '1000088395.png'
        };

        // High-Luxury Procedural Canvas Fallbacks (Used ONLY if the local PNG files aren't in the same folder yet)
        function createLuxuryFallbackDataURI(type) {
            const c = document.createElement('canvas');
            c.width = 1200;
            c.height = 1200;
            const ctx = c.getContext('2d');

            const drawPerfumeBottle = (bx, by, scale, opts = {}) => {
                ctx.save();
                ctx.translate(bx, by);
                ctx.scale(scale, scale);

                // Optional Luxury Box behind bottle
                if (opts.showBox) {
                    const boxGrad = ctx.createLinearGradient(-220, -210, -40, 180);
                    boxGrad.addColorStop(0, '#1c1c1c');
                    boxGrad.addColorStop(1, '#090909');
                    ctx.fillStyle = boxGrad;
                    ctx.strokeStyle = 'rgba(212,175,55,0.35)';
                    ctx.lineWidth = 2;
                    ctx.fillRect(-230, -210, 200, 360);
                    ctx.strokeRect(-230, -210, 200, 360);

                    ctx.fillStyle = '#d4af37';
                    ctx.font = '600 22px Cinzel, serif';
                    ctx.textAlign = 'center';
                    ctx.fillText('V E L O R A', -130, -45);
                    ctx.font = '400 10px Cinzel, serif';
                    ctx.fillText('EAU DE PARFUM', -130, -22);
                    ctx.font = '400 9px Cinzel, serif';
                    ctx.fillText('100 ML  e  3.4 FL.OZ.', -130, 125);
                }

                // Mist / Smoke effect
                if (opts.showSmoke) {
                    for (let i = 0; i < 12; i++) {
                        const rad = ctx.createRadialGradient(
                            Math.sin(i) * 90, -120 - (i * 10), 5,
                            Math.sin(i) * 90, -120 - (i * 10), 110
                        );
                        rad.addColorStop(0, 'rgba(225, 220, 210, 0.22)');
                        rad.addColorStop(1, 'rgba(225, 220, 210, 0)');
                        ctx.fillStyle = rad;
                        ctx.beginPath();
                        ctx.arc(Math.sin(i) * 90, -120 - (i * 10), 110, 0, Math.PI * 2);
                        ctx.fill();
                    }
                }

                // Gold Atomizer Collar
                const neckGrad = ctx.createLinearGradient(-28, -145, 28, -145);
                neckGrad.addColorStop(0, '#6e5211');
                neckGrad.addColorStop(0.5, '#f5e29c');
                neckGrad.addColorStop(1, '#7a5c14');
                ctx.fillStyle = neckGrad;
                ctx.fillRect(-26, -145, 52, 22);

                // Cap (Unless removed for atomizer shot)
                if (!opts.capOff) {
                    const capGrad = ctx.createLinearGradient(-56, -230, 56, -145);
                    capGrad.addColorStop(0, '#232323');
                    capGrad.addColorStop(0.5, '#0e0e0e');
                    capGrad.addColorStop(1, '#040404');
                    ctx.fillStyle = capGrad;
                    ctx.strokeStyle = 'rgba(255,255,255,0.16)';
                    ctx.lineWidth = 1.5;
                    ctx.fillRect(-56, -228, 112, 83);
                    ctx.strokeRect(-56, -228, 112, 83);

                    if (opts.showV) {
                        ctx.strokeStyle = '#d4af37';
                        ctx.lineWidth = 3;
                        ctx.beginPath();
                        ctx.moveTo(-18, -202);
                        ctx.lineTo(0, -172);
                        ctx.lineTo(18, -202);
                        ctx.stroke();
                    }
                } else {
                    // Sprayer Nozzle
                    ctx.fillStyle = neckGrad;
                    ctx.fillRect(-14, -175, 28, 30);
                }

                // Glass Bottle Outer Frame
                const glassGrad = ctx.createLinearGradient(0, -123, 0, 155);
                glassGrad.addColorStop(0, '#0b0908');
                glassGrad.addColorStop(0.45, '#1c130c');
                glassGrad.addColorStop(0.82, '#69421c');
                glassGrad.addColorStop(1, '#c88a3e');
                ctx.fillStyle = glassGrad;
                ctx.strokeStyle = 'rgba(243, 229, 171, 0.45)';
                ctx.lineWidth = 3;
                ctx.fillRect(-95, -123, 190, 278);
                ctx.strokeRect(-95, -123, 190, 278);

                // Inner Amber Chamber
                ctx.strokeStyle = 'rgba(212, 175, 55, 0.25)';
                ctx.lineWidth = 1.5;
                ctx.strokeRect(-82, -110, 164, 242);

                // Brand Typography on Bottle
                ctx.fillStyle = '#e5c878';
                ctx.font = '600 22px Cinzel, serif';
                ctx.textAlign = 'center';
                ctx.fillText('V E L O R A', 0, -5);
                ctx.font = '400 10px Cinzel, serif';
                ctx.fillText('EAU DE PARFUM', 0, 16);
                ctx.font = '400 9px Cinzel, serif';
                ctx.fillText('100 ML  e  3.4 FL.OZ.', 0, 142);

                // Water droplets if requested
                if (opts.droplets) {
                    ctx.fillStyle = 'rgba(255,255,255,0.45)';
                    for (let d = 0; d < 28; d++) {
                        ctx.beginPath();
                        ctx.arc((Math.sin(d * 7) * 80), -180 + (d * 11), (d % 3) + 1.5, 0, Math.PI * 2);
                        ctx.fill();
                    }
                }
                ctx.restore();
            };

            if (type === 'hero') {
                const bg = ctx.createRadialGradient(650, 450, 50, 600, 600, 850);
                bg.addColorStop(0, '#2a2218');
                bg.addColorStop(0.6, '#101010');
                bg.addColorStop(1, '#050505');
                ctx.fillStyle = bg;
                ctx.fillRect(0, 0, 1200, 1200);
                // Marble floor line
                ctx.fillStyle = '#090909';
                ctx.fillRect(0, 860, 1200, 340);
                drawPerfumeBottle(720, 620, 1.65, { showBox: true });
            } else if (type === 'grid9') {
                const configs = [
                    { bg: '#15120e', opts: {} },
                    { bg: '#382e22', opts: { showBox: true } },
                    { bg: '#0d0c0a', opts: { showV: true }, scale: 1.35 },
                    { bg: '#21160c', opts: {} },
                    { bg: '#141311', opts: {} },
                    { bg: '#101214', opts: {} },
                    { bg: '#121212', opts: { showBox: true } },
                    { bg: '#331f0a', opts: {}, scale: 1.45 },
                    { bg: '#3b2816', opts: { slogan: true } }
                ];
                configs.forEach((cfg, idx) => {
                    const col = idx % 3;
                    const row = Math.floor(idx / 3);
                    const x = col * 400;
                    const y = row * 400;
                    const g = ctx.createRadialGradient(x + 200, y + 180, 20, x + 200, y + 200, 280);
                    g.addColorStop(0, cfg.bg);
                    g.addColorStop(1, '#050505');
                    ctx.fillStyle = g;
                    ctx.fillRect(x, y, 400, 400);
                    drawPerfumeBottle(x + (cfg.opts.showBox ? 255 : 200), y + 235, cfg.scale || 0.72, cfg.opts);
                });
            } else if (type === 'grid6') {
                const configs = [
                    { bg: '#3a2612', opts: {} },
                    { bg: '#161616', opts: { showBox: true } },
                    { bg: '#0e0e11', opts: {} },
                    { bg: '#1c1915', opts: { capOff: true, showSmoke: true } },
                    { bg: '#2b2118', opts: {} },
                    { bg: '#121314', opts: { droplets: true, showV: true }, scale: 1.15 }
                ];
                configs.forEach((cfg, idx) => {
                    const col = idx % 3;
                    const row = Math.floor(idx / 3);
                    const x = col * 400;
                    const y = row * 600;
                    const g = ctx.createRadialGradient(x + 200, y + 280, 30, x + 200, y + 300, 360);
                    g.addColorStop(0, cfg.bg);
                    g.addColorStop(1, '#050505');
                    ctx.fillStyle = g;
                    ctx.fillRect(x, y, 400, 600);
                    drawPerfumeBottle(x + (cfg.opts.showBox ? 255 : 200), y + 340, cfg.scale || 0.88, cfg.opts);
                });
            }
            return c.toDataURL('image/png');
        }

        // Metadata for all 15 Sliced Interactive Shots (9 from 1000088394.png + 6 from 1000088395.png)
        const SLICED_GALLERY_ITEMS = [
            // 9 Shots from 1000088394.png (3x3 Grid)
            { id: 1, grid: 'grid9', pos: '0% 0%', category: 'nature', badge: 'الشبكة 1 • زاوية 1', title: 'شموخ الصخور البركانية', desc: 'زجاجة VELORA تستقر فوق صخور داكنة تحت شعاع ضوئي درامي يبرز حواف الكريستال.' },
            { id: 2, grid: 'grid9', pos: '50% 0%', category: 'luxury', badge: 'الشبكة 1 • زاوية 2', title: 'ظلال النخيل وضوء النهار', desc: 'تناغم العلبة السوداء والزجاجة الكهرمانية مع ظلال الطبيعة الدافئة على الرخام.' },
            { id: 3, grid: 'grid9', pos: '100% 0%', category: 'macro', badge: 'الشبكة 1 • زاوية 3', title: 'ماكرو شعار (V) المحفور', desc: 'لقطة مقربة جداً لقمة الغطاء الأسود تبرز دقة حفر شعار V والطوق الذهبي.' },
            { id: 4, grid: 'grid9', pos: '0% 50%', category: 'nature', badge: 'الشبكة 1 • زاوية 4', title: 'أخشاب العود والياسمين الأبيض', desc: 'استعراض المكونات الخام للعطر من كسر العود المعتق، الأزهار البيضاء، وحبوب القهوة.' },
            { id: 5, grid: 'grid9', pos: '50% 50%', category: 'luxury', badge: 'الشبكة 1 • زاوية 5', title: 'منصة التتويج الملكية', desc: 'حضور مسرحي للزجاجة فوق منصة حجرية سوداء وتحت شعار VELORA الذهبي.' },
            { id: 6, grid: 'grid9', pos: '100% 50%', category: 'luxury', badge: 'الشبكة 1 • زاوية 6', title: 'الأناقة المعمارية المعاصرة', desc: 'انعكاس الزجاجة على الرخام الأسود المجزع بجانب عناصر ديكور فنية فاخرة.' },
            { id: 7, grid: 'grid9', pos: '0% 100%', category: 'luxury', badge: 'الشبكة 1 • زاوية 7', title: 'ثنائية العلبة والزجاجة', desc: 'لقطة علوية تبرز текстуر الورق الأسود الفاخر للعلبة بجانب لمعان الزجاج.' },
            { id: 8, grid: 'grid9', pos: '50% 100%', category: 'macro', badge: 'الشبكة 1 • زاوية 8', title: 'توهج السائل الكهرماني', desc: 'لقطة ماكرو ساحرة تكشف دفء اللون العنبري الذهبي في قاعدة الزجاجة السميكة.' },
            { id: 9, grid: 'grid9', pos: '100% 100%', category: 'nature', badge: 'الشبكة 1 • زاوية 9', title: 'إطلالة الغروب — It\'s A Presence', desc: 'اللقطة الأيقونية لشعار العلامة MORE THAN A FRAGRANCE, IT\'S A PRESENCE عند قمم الجبال.' },

            // 6 Shots from 1000088395.png (3x2 Grid)
            { id: 10, grid: 'grid6', pos: '0% 0%', category: 'nature', badge: 'الشبكة 2 • زاوية 1', title: 'دفء الشمس الذهبية', desc: 'إضاءة خلفية دافئة تخترق زجاج VELORA لتشعل بريق الكهرمان.' },
            { id: 11, grid: 'grid6', pos: '50% 0%', category: 'luxury', badge: 'الشبكة 2 • زاوية 2', title: 'الخط الذهبي الكلاسيكي', desc: 'استعراض رسمي يجمع الزجاجة مع العلبة المزينة بخط ذهبي عمودي أنيق.' },
            { id: 12, grid: 'grid6', pos: '100% 0%', category: 'luxury', badge: 'الشبكة 2 • زاوية 3', title: 'نعومة الحرير الأسود', desc: 'الزجاجة تتوسد طيات قماش الساتان والحرير الأسود في مشهد يعكس النعومة والعمق.' },
            { id: 13, grid: 'grid6', pos: '0% 100%', category: 'macro', badge: 'الشبكة 2 • زاوية 4', title: 'سحابة البخور والبخاخ الذهبي', desc: 'الغطاء الأسود مفصولاً عن الزجاجة ليظهر البخاخ الذهبي محاطاً بدخان عطري ساحر.' },
            { id: 14, grid: 'grid6', pos: '50% 100%', category: 'nature', badge: 'الشبكة 2 • زاوية 5', title: 'أصالة الأرض والطبيعة الخام', desc: 'توازن بصري بين صقل الزجاجة الهندسي وخشونة الصخور والأخشاب الطبيعية.' },
            { id: 15, grid: 'grid6', pos: '100% 100%', category: 'macro', badge: 'الشبكة 2 • زاوية 6', title: 'قطرات الندى الباردة', desc: 'لقطة ماكرو بزاوية مائلة تبرز قطرات الماء النقية فوق الغطاء الأسود وكتف الزجاجة.' }
        ];

        // Hotspots Data for Hero Image (1000088393.png)
        const HOTSPOTS_DATA = [
            {
                badge: 'نقطة تفاعلية 01 / 04 • القمة',
                title: 'الغطاء الأسود المحفور بحرف (V)',
                desc: 'غطاء هندسي مربع بلون الأوبسيديان الأسود المطفي، يتوسط قمته شعار حرف V المحفور بدقة مع طوق ذهبي مصقول يعكس الفخامة.'
            },
            {
                badge: 'نقطة تفاعلية 02 / 04 • البخاخ',
                title: 'فوهة الرذاذ الذهبية (Atomizer)',
                desc: 'عنق معدني مطلي بالذهب المصقول يضم مضخة رذاذ متطورة تطلق سحابة عطرية ناعمة ومتجانسة عند كل رشة.'
            },
            {
                badge: 'نقطة تفاعلية 03 / 04 • الزجاج والسائل',
                title: 'زجاج كهرماني متدرج (100 ML - 3.4 FL.OZ.)',
                desc: 'زجاج ثقيل بتدرج لوني من الأسود الدخاني إلى العنبر الذهبي لحماية تركيز Eau De Parfum وإبراز توهج العطر.'
            },
            {
                badge: 'نقطة تفاعلية 04 / 04 • التغليف',
                title: 'العلبة السوداء ذات الملمس البارز',
                desc: 'علبة فاخرة مصنوعة من الورق الأسود ذي الملمس الجلدي الناعم مع طباعة حرارية ذهبية لاسم VELORA.'
            }
        ];

        // Olfactory Notes Data
        const OLFACTORY_DATA = [
            {
                grid: 'grid6',
                pos: '100% 100%',
                tag: 'اللقطة المعبّرة: قطرات الندى على الغطاء',
                quote: '"انتعاش يوقظ الحواس منذ اللحظة الأولى لملامسة العطر للبشرة."',
                ambient: 'rgba(120, 190, 235, 0.16)',
                particleMode: 'dew'
            },
            {
                grid: 'grid9',
                pos: '0% 50%',
                tag: 'اللقطة المعبّرة: الأزهار البيضاء والعود والقهوة',
                quote: '"قلب عطري نابض يجمع بين نقاء الياسمين الأبيض وغموض الدخان العطري."',
                ambient: 'rgba(212, 175, 55, 0.20)',
                particleMode: 'smoke'
            },
            {
                grid: 'grid9',
                pos: '100% 100%',
                tag: 'اللقطة المعبّرة: توهج الغروب — It\'s A Presence',
                quote: '"قاعدة كهرمانية خشبية عميقة تمنحك حضوراً مهيباً يدوم لساعات طويلة."',
                ambient: 'rgba(184, 115, 51, 0.24)',
                particleMode: 'amber'
            }
        ];

        let loupeEnabled = true;
        let currentFilter = 'all';
        let soundEnabled = true;

        // Handle fallback if local file is missing before user uploads
        function handleImageFallback(imgEl, key) {
            const fallbackURI = createLuxuryFallbackDataURI(key);
            imageSources[key] = fallbackURI;
            imgEl.src = fallbackURI;
            applyImagesToAllSlicedElements();
        }

        // Pre-check grid images and apply fallback if not found locally
        function preloadGridImage(key) {
            const testImg = new Image();
            testImg.onload = () => {
                applyImagesToAllSlicedElements();
            };
            testImg.onerror = () => {
                imageSources[key] = createLuxuryFallbackDataURI(key);
                applyImagesToAllSlicedElements();
            };
            testImg.src = imageSources[key];
        }

        // Render the 15 Sliced Cards into the Gallery
        function renderSlicedGallery() {
            const container = document.getElementById('slicedGalleryGrid');
            const filtered = currentFilter === 'all'
                ? SLICED_GALLERY_ITEMS
                : SLICED_GALLERY_ITEMS.filter(item => item.category === currentFilter);

            container.innerHTML = filtered.map(item => {
                const sliceClass = item.grid === 'grid9' ? 'sliced-photo-3x3' : 'sliced-photo-3x2';
                const bgUrl = imageSources[item.grid];
                return `
                    <div class="gallery-card ${loupeEnabled ? 'loupe-enabled' : ''} group relative rounded-3xl overflow-hidden luxury-glass border border-white/10 hover:border-gold/50 transition-all duration-300 flex flex-col"
                         onmousemove="handleLoupeMove(event, this, '${item.grid}', '${item.pos}')"
                         onclick="openSlicedLightbox('${item.grid}', '${item.pos}', '${item.title.replace(/'/g, "\\'")}', '${item.desc.replace(/'/g, "\\'")}')">
                        
                        <div class="relative aspect-square overflow-hidden bg-obsidian cursor-pointer">
                            <!-- Sliced Background Layer -->
                            <div class="${sliceClass} w-full h-full" 
                                 data-grid="${item.grid}" 
                                 style="background-image: url('${bgUrl}'); background-position: ${item.pos};">
                            </div>

                            <!-- Interactive Magnifying Glass Loupe -->
                            <div class="loupe-lens" style="background-image: url('${bgUrl}');"></div>

                            <!-- Subtle Top Badge -->
                            <div class="absolute top-3.5 right-3.5 z-20 px-3 py-1 rounded-full bg-black/75 backdrop-blur-md border border-gold/30 text-[11px] text-gold-light">
                                ${item.badge}
                            </div>

                            <!-- Expand Icon -->
                            <div class="absolute top-3.5 left-3.5 z-20 w-8 h-8 rounded-full bg-black/70 text-white/80 group-hover:bg-gold group-hover:text-obsidian flex items-center justify-center text-xs transition">
                                <i class="fa-solid fa-expand"></i>
                            </div>
                        </div>

                        <div class="p-5 flex-1 flex flex-col justify-between bg-gradient-to-b from-[#121212] to-[#0a0a0a]">
                            <div>
                                <h3 class="text-lg font-bold text-white group-hover:text-gold transition">${item.title}</h3>
                                <p class="text-xs text-stone-400 mt-1.5 leading-relaxed">${item.desc}</p>
                            </div>
                            <div class="mt-4 pt-3 border-t border-white/5 flex items-center justify-between text-[11px] text-gold/80">
                                <span>انقر للعرض الكامل</span>
                                <span class="font-luxury">VELORA 100ML</span>
                            </div>
                        </div>
                    </div>
                `;
            }).join('');
        }

        // Apply updated image URLs to all sliced elements on the page
        function applyImagesToAllSlicedElements() {
            const heroImg = document.getElementById('heroMainImg');
            if (heroImg) heroImg.src = imageSources.hero;

            document.querySelectorAll('[data-grid="grid9"]').forEach(el => {
                el.style.backgroundImage = `url('${imageSources.grid9}')`;
            });
            document.querySelectorAll('[data-grid="grid6"]').forEach(el => {
                el.style.backgroundImage = `url('${imageSources.grid6}')`;
            });
            renderSlicedGallery();
            if (typeof update3DBackdropTextures === 'function') {
                update3DBackdropTextures();
            }
        }

        // Magnifying Loupe Calculation for Sliced Sprites
        function handleLoupeMove(e, cardEl, gridKey, posStr) {
            if (!loupeEnabled) return;
            const lens = cardEl.querySelector('.loupe-lens');
            const rect = cardEl.querySelector('.aspect-square').getBoundingClientRect();
            const relX = Math.max(0, Math.min(1, (e.clientX - rect.left) / rect.width));
            const relY = Math.max(0, Math.min(1, (e.clientY - rect.top) / rect.height));

            lens.style.left = `${e.clientX - rect.left}px`;
            lens.style.top = `${e.clientY - rect.top}px`;

            // Map relative position inside the cell to the full 3x3 or 3x2 sheet
            const [colPct, rowPct] = posStr.split(' ').map(s => parseFloat(s));
            const colIndex = colPct === 0 ? 0 : colPct === 50 ? 1 : 2;
            const rowIndex = rowPct === 0 ? 0 : (gridKey === 'grid9' ? (rowPct === 50 ? 1 : 2) : 1);

            const sheetX = ((colIndex + relX) / 3) * 100;
            const totalRows = gridKey === 'grid9' ? 3 : 2;
            const sheetY = ((rowIndex + relY) / totalRows) * 100;

            lens.style.backgroundSize = gridKey === 'grid9' ? '650% 650%' : '650% 440%';
            lens.style.backgroundPosition = `${sheetX}% ${sheetY}%`;
        }

        function toggleLoupeMode() {
            loupeEnabled = !loupeEnabled;
            const statusText = document.getElementById('loupeStatusText');
            const btn = document.getElementById('loupeToggleBtn');
            statusText.textContent = loupeEnabled ? 'عدسة المجهر التفاعلية: مفعّلة' : 'عدسة المجهر التفاعلية: متوقفة';
            btn.classList.toggle('bg-gold', loupeEnabled);
            btn.classList.toggle('text-obsidian', loupeEnabled);
            renderSlicedGallery();
        }

        function filterGallery(cat, btnEl) {
            currentFilter = cat;
            document.querySelectorAll('.filter-tab').forEach(b => {
                b.className = 'filter-tab px-4 py-2 rounded-full bg-white/5 text-stone-300 hover:bg-white/10 text-xs sm:text-sm transition';
            });
            btnEl.className = 'filter-tab active px-4 py-2 rounded-full bg-gold text-obsidian font-bold text-xs sm:text-sm transition';
            renderSlicedGallery();
        }

        // Hero Hotspot Selector
        function selectHotspot(index, pinEl) {
            document.querySelectorAll('.hotspot-pin').forEach(p => p.classList.remove('active'));
            pinEl.classList.add('active');

            const data = HOTSPOTS_DATA[index];
            const panel = document.getElementById('hotspotInfoPanel');
            panel.classList.add('scale-[0.98]', 'opacity-80');
            setTimeout(() => {
                document.getElementById('hotspotBadge').innerHTML = `<i class="fa-solid fa-hand-pointer ml-1"></i> ${data.badge}`;
                document.getElementById('hotspotTitle').textContent = data.title;
                document.getElementById('hotspotDesc').textContent = data.desc;
                panel.classList.remove('scale-[0.98]', 'opacity-80');
            }, 120);
        }

        // Interactive Olfactory Pyramid Switcher
        function selectOlfactoryNote(idx) {
            const data = OLFACTORY_DATA[idx];
            document.querySelectorAll('.olfactory-btn').forEach((btn, i) => {
                if (i === idx) {
                    btn.className = 'olfactory-btn w-full text-right p-6 rounded-2xl luxury-glass border-2 border-gold transition-all flex items-start gap-4 shadow-lg shadow-gold/10';
                } else {
                    btn.className = 'olfactory-btn w-full text-right p-6 rounded-2xl luxury-glass border border-white/10 hover:border-gold/40 transition-all flex items-start gap-4';
                }
            });

            const visual = document.getElementById('olfactoryVisual');
            visual.className = `${data.grid === 'grid9' ? 'sliced-photo-3x3' : 'sliced-photo-3x2'} w-full h-full transition-all duration-700`;
            visual.setAttribute('data-grid', data.grid);
            visual.style.backgroundImage = `url('${imageSources[data.grid]}')`;
            visual.style.backgroundPosition = data.pos;

            document.getElementById('olfactoryStageTag').textContent = data.tag;
            document.getElementById('olfactoryStageQuote').textContent = data.quote;
            document.documentElement.style.setProperty('--ambient-color', data.ambient);

            triggerPerfumeSpray(data.particleMode);
        }

        // Lightbox Controls
        function openLightbox(key, title, desc) {
            const modal = document.getElementById('lightboxModal');
            const visual = document.getElementById('lightboxVisual');
            visual.className = 'w-full h-full bg-center bg-cover bg-no-repeat transition-transform duration-500 hover:scale-110 cursor-zoom-in';
            visual.style.backgroundImage = `url('${imageSources[key]}')`;
            visual.style.backgroundSize = 'cover';
            visual.style.backgroundPosition = 'center';

            document.getElementById('lightboxTitle').textContent = title;
            document.getElementById('lightboxDesc').textContent = desc;
            modal.classList.remove('hidden');
            modal.classList.add('flex');
        }

        function openSlicedLightbox(gridKey, pos, title, desc) {
            const modal = document.getElementById('lightboxModal');
            const visual = document.getElementById('lightboxVisual');
            visual.className = `${gridKey === 'grid9' ? 'sliced-photo-3x3' : 'sliced-photo-3x2'} w-full h-full transition-transform duration-500 hover:scale-110 cursor-zoom-in`;
            visual.style.backgroundImage = `url('${imageSources[gridKey]}')`;
            visual.style.backgroundPosition = pos;

            document.getElementById('lightboxTitle').textContent = title;
            document.getElementById('lightboxDesc').textContent = desc;
            modal.classList.remove('hidden');
            modal.classList.add('flex');
        }

        function closeLightbox() {
            const modal = document.getElementById('lightboxModal');
            modal.classList.add('hidden');
            modal.classList.remove('flex');
        }

        // Image Manager & Multi-File Smart Upload
        function openImageManagerModal() {
            const m = document.getElementById('imageManagerModal');
            m.classList.remove('hidden');
            m.classList.add('flex');
        }
        function closeImageManagerModal() {
            const m = document.getElementById('imageManagerModal');
            m.classList.add('hidden');
            m.classList.remove('flex');
        }

        function updateSpecificImage(slot, inputEl) {
            if (!inputEl.files || !inputEl.files[0]) return;
            const url = URL.createObjectURL(inputEl.files[0]);
            imageSources[slot] = url;
            applyImagesToAllSlicedElements();
        }

        // Multi-file listener: sorts by filename or order (1 -> hero, 2 -> grid9, 3 -> grid6)
        document.getElementById('multiImageInput').addEventListener('change', function(e) {
            const files = Array.from(e.target.files || []);
            if (!files.length) return;

            files.sort((a, b) => a.name.localeCompare(b.name));
            files.forEach((file, idx) => {
                const url = URL.createObjectURL(file);
                if (file.name.includes('93') || idx === 0) imageSources.hero = url;
                else if (file.name.includes('94') || idx === 1) imageSources.grid9 = url;
                else if (file.name.includes('95') || idx === 2) imageSources.grid6 = url;
            });
            applyImagesToAllSlicedElements();
            triggerPerfumeSpray();
        });

        // Code Modal & Copy
        function toggleCodeModal(show) {
            const m = document.getElementById('codeModal');
            m.classList.toggle('hidden', !show);
            m.classList.toggle('flex', show);
        }

        function copyScriptSnippet() {
            const text = document.getElementById('snippetBox').innerText;
            const temp = document.createElement('textarea');
            temp.value = text;
            document.body.appendChild(temp);
            temp.select();
            document.execCommand('copy');
            document.body.removeChild(temp);
            const btn = document.getElementById('copyBtnText');
            btn.innerHTML = '<i class="fa-solid fa-check ml-1"></i> تم النسخ بنجاح!';
            setTimeout(() => {
                btn.innerHTML = '<i class="fa-solid fa-copy ml-1"></i> نسخ السكربت';
            }, 2000);
        }

        // ==========================================
        // 3D TILT ENGINE FOR HERO SHOWCASE
        // ==========================================
        const heroCard = document.getElementById('heroTiltCard');
        const heroSpotlight = document.getElementById('heroSpotlight');

        if (heroCard) {
            heroCard.addEventListener('mousemove', (e) => {
                const rect = heroCard.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                const centerX = rect.width / 2;
                const centerY = rect.height / 2;

                const rotateX = ((y - centerY) / centerY) * -9;
                const rotateY = ((x - centerX) / centerX) * 9;

                heroCard.style.transform = `rotateX(${rotateX.toFixed(2)}deg) rotateY(${rotateY.toFixed(2)}deg)`;
                heroSpotlight.style.opacity = '1';
                heroSpotlight.style.background = `radial-gradient(420px circle at ${x}px ${y}px, rgba(212, 175, 55, 0.25), transparent 70%)`;
            });

            heroCard.addEventListener('mouseleave', () => {
                heroCard.style.transform = 'rotateX(0deg) rotateY(0deg)';
                heroSpotlight.style.opacity = '0';
            });
        }

        // ==========================================
        // WEB AUDIO API: SUBTLE LUXURY ATOMIZER SPRAY SOUND
        // ==========================================
        function playSpraySound() {
            if (!soundEnabled) return;
            try {
                const AudioCtx = window.AudioContext || window.webkitAudioContext;
                const ctx = new AudioCtx();
                const duration = 0.55;
                const bufferSize = ctx.sampleRate * duration;
                const buffer = ctx.createBuffer(1, bufferSize, ctx.sampleRate);
                const data = buffer.getChannelData(0);
                for (let i = 0; i < bufferSize; i++) {
                    data[i] = (Math.random() * 2 - 1) * Math.exp(-i / (ctx.sampleRate * 0.18));
                }

                const noise = ctx.createBufferSource();
                noise.buffer = buffer;

                const filter = ctx.createBiquadFilter();
                filter.type = 'bandpass';
                filter.frequency.setValueAtTime(2800, ctx.currentTime);
                filter.Q.setValueAtTime(1.8, ctx.currentTime);

                const gain = ctx.createGain();
                gain.gain.setValueAtTime(0.18, ctx.currentTime);
                gain.gain.exponentialRampToValueAtTime(0.001, ctx.currentTime + duration);

                noise.connect(filter);
                filter.connect(gain);
                gain.connect(ctx.destination);
                noise.start();
            } catch (err) {
                // Ignore if browser blocks audio before interaction
            }
        }

        function toggleAudio() {
            soundEnabled = !soundEnabled;
            const icon = document.getElementById('soundIcon');
            icon.className = soundEnabled ? 'fa-solid fa-volume-high text-xs' : 'fa-solid fa-volume-xmark text-xs text-stone-500';
        }

        // ==========================================
        // HTML5 CANVAS GOLDEN MIST & INCENSE PARTICLE SYSTEM
        // ==========================================
        const canvas = document.getElementById('aromaCanvas');
        const ctx = canvas.getContext('2d');
        let particles = [];

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        function createParticle(x, y, mode = 'gold', burst = false) {
            const angle = burst ? (Math.random() * Math.PI - Math.PI) : (Math.random() * Math.PI * 2);
            const speed = burst ? (Math.random() * 6 + 1.5) : (Math.random() * 0.6 + 0.15);
            let color = '212, 175, 55';
            if (mode === 'dew') color = '180, 225, 255';
            else if (mode === 'smoke') color = '235, 230, 220';
            else if (mode === 'amber') color = '205, 130, 50';

            return {
                x,
                y,
                vx: Math.cos(angle) * speed,
                vy: burst ? (Math.sin(angle) * speed - 1.5) : (-Math.random() * 0.7 - 0.1),
                radius: burst ? (Math.random() * 22 + 3) : (Math.random() * 2.5 + 0.8),
                alpha: burst ? 0.55 : (Math.random() * 0.45 + 0.1),
                decay: burst ? (Math.random() * 0.012 + 0.006) : 0.002,
                color,
                isMist: burst && Math.random() > 0.35
            };
        }

        // Seed subtle floating ambient golden dust
        for (let i = 0; i < 28; i++) {
            particles.push(createParticle(Math.random() * window.innerWidth, Math.random() * window.innerHeight, 'gold', false));
        }

        function triggerPerfumeSpray(mode = 'gold') {
            playSpraySound();
            const originX = window.innerWidth * 0.35;
            const originY = window.innerHeight * 0.45;
            for (let i = 0; i < 65; i++) {
                particles.push(createParticle(originX, originY, mode, true));
            }
        }

        function animateAromaLoop() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            for (let i = particles.length - 1; i >= 0; i--) {
                const p = particles[i];
                p.x += p.vx;
                p.y += p.vy;
                p.alpha -= p.decay;

                if (p.isMist) {
                    p.radius += 0.35;
                    const grad = ctx.createRadialGradient(p.x, p.y, 1, p.x, p.y, p.radius);
                    grad.addColorStop(0, `rgba(${p.color}, ${Math.max(0, p.alpha * 0.45)})`);
                    grad.addColorStop(1, `rgba(${p.color}, 0)`);
                    ctx.fillStyle = grad;
                    ctx.beginPath();
                    ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
                    ctx.fill();
                } else {
                    ctx.fillStyle = `rgba(${p.color}, ${Math.max(0, p.alpha)})`;
                    ctx.beginPath();
                    ctx.arc(p.x, p.y, p.radius, 0, Math.PI * 2);
                    ctx.fill();
                }

                if (p.alpha <= 0) {
                    particles.splice(i, 1);
                }
            }

            // Maintain gentle ambient golden particles
            if (particles.length < 25) {
                particles.push(createParticle(Math.random() * canvas.width, canvas.height + 10, 'gold', false));
            }

            requestAnimationFrame(animateAromaLoop);
        }

        // ==========================================
        // THREE.JS 360° 3D PERFUME & PRODUCT LINEUP ENGINE
        // ==========================================
        let scene3D, camera3D, renderer3D;
        let podiumGroup, bottleGroup, capGroup, sprayerHeadMesh, liquidMesh, boxGroup, travelAtomizerGroup, photoMonolithGroup;
        let pointLightGold, pointLightAmber, spotLightMain;
        let isCapOpen = false;
        let isExploded = false;
        let autoRotate3D = true;
        let productLineupMode = 0; // 0: Full Set (Bottle + Box + Travel Spray), 1: Solo Bottle, 2: Bottle + 3D Photo Monoliths
        let sprayParticles3D = [];

        // Camera spherical coordinates for smooth mouse/touch orbit
        let camTheta = 0.35;
        let camPhi = 1.32;
        let camRadius = 9.2;
        let targetTheta = 0.35;
        let targetPhi = 1.32;
        let targetRadius = 9.2;
        let camLookY = 0.6;
        let targetLookY = 0.6;

        // Generate High-Resolution Procedural Textures for the 3D Models
        function createFrontBottleLabelTexture() {
            const c = document.createElement('canvas');
            c.width = 1024;
            c.height = 1280;
            const ctx = c.getContext('2d');

            // Subtle smoked-to-amber glass gradient with border sheen
            const grad = ctx.createLinearGradient(0, 0, 0, 1280);
            grad.addColorStop(0, 'rgba(8, 7, 6, 0.92)');
            grad.addColorStop(0.5, 'rgba(26, 17, 9, 0.78)');
            grad.addColorStop(0.85, 'rgba(120, 74, 26, 0.68)');
            grad.addColorStop(1, 'rgba(205, 138, 54, 0.85)');
            ctx.fillStyle = grad;
            ctx.fillRect(0, 0, 1024, 1280);

            // Inner glass frame highlight
            ctx.strokeStyle = 'rgba(243, 229, 171, 0.35)';
            ctx.lineWidth = 10;
            ctx.strokeRect(56, 56, 912, 1168);

            // Gold Metallic Typography: VELORA
            ctx.fillStyle = '#e7c97a';
            ctx.textAlign = 'center';
            ctx.font = '600 92px Cinzel, serif';
            ctx.fillText('V E L O R A', 512, 520);

            ctx.font = '400 38px Cinzel, serif';
            ctx.fillStyle = '#d8b768';
            ctx.fillText('E A U   D E   P A R F U M', 512, 600);

            // Bottom Volume Engraving
            ctx.font = '400 32px Cinzel, serif';
            ctx.fillStyle = 'rgba(231, 201, 122, 0.85)';
            ctx.fillText('100 ML   e   3.4 FL.OZ.', 512, 1150);

            const tex = new THREE.CanvasTexture(c);
            tex.anisotropy = 4;
            return tex;
        }

        function createCapTopVTexture() {
            const c = document.createElement('canvas');
            c.width = 512;
            c.height = 512;
            const ctx = c.getContext('2d');

            // Matte obsidian surface
            ctx.fillStyle = '#0d0d0d';
            ctx.fillRect(0, 0, 512, 512);

            // Subtle beveled border
            ctx.strokeStyle = 'rgba(255, 255, 255, 0.12)';
            ctx.lineWidth = 8;
            ctx.strokeRect(18, 18, 476, 476);

            // Engraved 'V' Logo in center
            ctx.strokeStyle = '#d4af37';
            ctx.lineWidth = 16;
            ctx.lineCap = 'round';
            ctx.lineJoin = 'miter';
            ctx.beginPath();
            ctx.moveTo(175, 165);
            ctx.lineTo(256, 355);
            ctx.lineTo(337, 165);
            ctx.stroke();

            return new THREE.CanvasTexture(c);
        }

        function createLuxuryBoxTexture() {
            const c = document.createElement('canvas');
            c.width = 1024;
            c.height = 1536;
            const ctx = c.getContext('2d');

            // Matte black grained paper background
            const g = ctx.createLinearGradient(0, 0, 1024, 1536);
            g.addColorStop(0, '#181818');
            g.addColorStop(0.5, '#0e0e0e');
            g.addColorStop(1, '#070707');
            ctx.fillStyle = g;
            ctx.fillRect(0, 0, 1024, 1536);

            // Subtle grain dots
            ctx.fillStyle = 'rgba(255,255,255,0.02)';
            for (let i = 0; i < 4000; i++) {
                ctx.fillRect(Math.random() * 1024, Math.random() * 1536, 2, 2);
            }

            // Gold accent vertical line (seen in 1000088395.png top-center shot)
            const lineGrad = ctx.createLinearGradient(0, 0, 0, 1536);
            lineGrad.addColorStop(0, '#7a5c14');
            lineGrad.addColorStop(0.5, '#f3e5ab');
            lineGrad.addColorStop(1, '#7a5c14');
            ctx.fillStyle = lineGrad;
            ctx.fillRect(110, 0, 8, 1536);

            // Gold Foil Typography
            ctx.fillStyle = '#dfc072';
            ctx.textAlign = 'center';
            ctx.font = '600 90px Cinzel, serif';
            ctx.fillText('V E L O R A', 540, 640);

            ctx.font = '400 36px Cinzel, serif';
            ctx.fillText('E A U   D E   P A R F U M', 540, 725);

            ctx.font = '400 32px Cinzel, serif';
            ctx.fillStyle = 'rgba(223, 192, 114, 0.85)';
            ctx.fillText('100 ML   e   3.4 FL.OZ.', 540, 1380);

            return new THREE.CanvasTexture(c);
        }

        function createMarblePodiumTexture() {
            const c = document.createElement('canvas');
            c.width = 1024;
            c.height = 1024;
            const ctx = c.getContext('2d');

            ctx.fillStyle = '#090909';
            ctx.fillRect(0, 0, 1024, 1024);

            // Procedural white & gold marble veins
            for (let v = 0; v < 26; v++) {
                ctx.strokeStyle = v % 3 === 0 ? 'rgba(212, 175, 55, 0.22)' : 'rgba(255, 255, 255, 0.08)';
                ctx.lineWidth = Math.random() * 4 + 1;
                ctx.beginPath();
                let x = Math.random() * 1024;
                let y = Math.random() * 1024;
                ctx.moveTo(x, y);
                for (let s = 0; s < 8; s++) {
                    x += (Math.random() - 0.5) * 260;
                    y += (Math.random() - 0.5) * 260;
                    ctx.lineTo(x, y);
                }
                ctx.stroke();
            }
            return new THREE.CanvasTexture(c);
        }

        function initVelora3DStudio() {
            const container = document.getElementById('velora3DContainer');
            if (!container || typeof THREE === 'undefined') return;

            const w = container.clientWidth || 800;
            const h = container.clientHeight || 560;

            scene3D = new THREE.Scene();
            scene3D.fog = new THREE.FogExp2(0x070605, 0.045);

            camera3D = new THREE.PerspectiveCamera(38, w / h, 0.1, 100);

            renderer3D = new THREE.WebGLRenderer({ antialias: true, alpha: true });
            renderer3D.setSize(w, h);
            renderer3D.setPixelRatio(Math.min(window.devicePixelRatio, 2));
            renderer3D.shadowMap.enabled = true;
            container.innerHTML = '';
            container.appendChild(renderer3D.domElement);

            // Studio Lighting Setup
            const ambientLight = new THREE.AmbientLight(0xffffff, 0.65);
            scene3D.add(ambientLight);

            spotLightMain = new THREE.SpotLight(0xfff1d0, 2.2);
            spotLightMain.position.set(6, 11, 8);
            spotLightMain.castShadow = true;
            scene3D.add(spotLightMain);

            pointLightGold = new THREE.PointLight(0xd4af37, 1.9, 18);
            pointLightGold.position.set(-5, 3, 5);
            scene3D.add(pointLightGold);

            pointLightAmber = new THREE.PointLight(0xc87a28, 2.4, 14);
            pointLightAmber.position.set(0, -1.2, -4);
            scene3D.add(pointLightAmber);

            // Root Podium Group (Rotates smoothly)
            podiumGroup = new THREE.Group();
            scene3D.add(podiumGroup);

            // 1. Black & Gold Marble Podium Base
            const marbleTex = createMarblePodiumTexture();
            const podiumMat = new THREE.MeshStandardMaterial({
                map: marbleTex,
                roughness: 0.18,
                metalness: 0.25
            });
            const podiumGeo = new THREE.CylinderGeometry(4.4, 4.7, 0.45, 64);
            const podiumMesh = new THREE.Mesh(podiumGeo, podiumMat);
            podiumMesh.position.y = -2.15;
            podiumMesh.receiveShadow = true;
            podiumGroup.add(podiumMesh);

            // Gold Trim Ring around Podium
            const ringGeo = new THREE.TorusGeometry(4.42, 0.035, 16, 100);
            const goldMetalMat = new THREE.MeshStandardMaterial({
                color: 0xe5c158,
                metalness: 0.92,
                roughness: 0.16
            });
            const ringMesh = new THREE.Mesh(ringGeo, goldMetalMat);
            ringMesh.rotation.x = Math.PI / 2;
            ringMesh.position.y = -1.94;
            podiumGroup.add(ringMesh);

            // ==========================================
            // 2. MAIN VELORA 100ML 3D PERFUME BOTTLE
            // ==========================================
            bottleGroup = new THREE.Group();
            bottleGroup.position.set(0.85, -1.9, 0.35);
            podiumGroup.add(bottleGroup);

            const frontLabelTex = createFrontBottleLabelTexture();
            const darkGlassMat = new THREE.MeshStandardMaterial({
                color: 0x16100b,
                roughness: 0.08,
                metalness: 0.35,
                transparent: true,
                opacity: 0.92
            });
            const frontGlassMat = new THREE.MeshStandardMaterial({
                map: frontLabelTex,
                roughness: 0.08,
                metalness: 0.25
            });

            // Multi-material array for BoxGeometry [right, left, top, bottom, front, back]
            const flaconMaterials = [
                darkGlassMat,
                darkGlassMat,
                darkGlassMat,
                darkGlassMat,
                frontGlassMat,
                darkGlassMat
            ];

            const flaconGeo = new THREE.BoxGeometry(2.15, 2.95, 1.05);
            const flaconMesh = new THREE.Mesh(flaconGeo, flaconMaterials);
            flaconMesh.position.y = 1.48;
            flaconMesh.castShadow = true;
            bottleGroup.add(flaconMesh);

            // Thick Crystal Amber Base Glow
            const crystalBaseGeo = new THREE.BoxGeometry(2.17, 0.36, 1.07);
            const crystalBaseMat = new THREE.MeshStandardMaterial({
                color: 0xd4943a,
                emissive: 0x5c3409,
                emissiveIntensity: 0.55,
                roughness: 0.12,
                metalness: 0.2,
                transparent: true,
                opacity: 0.88
            });
            const crystalBaseMesh = new THREE.Mesh(crystalBaseGeo, crystalBaseMat);
            crystalBaseMesh.position.y = 0.18;
            bottleGroup.add(crystalBaseMesh);

            // Inner Glowing Amber Perfume Core (Visible especially in Exploded View)
            const liquidGeo = new THREE.BoxGeometry(1.78, 2.35, 0.72);
            const liquidMat = new THREE.MeshStandardMaterial({
                color: 0xb8732a,
                emissive: 0x6e3b0c,
                emissiveIntensity: 0.45,
                roughness: 0.15,
                metalness: 0.1,
                transparent: true,
                opacity: 0.9
            });
            liquidMesh = new THREE.Mesh(liquidGeo, liquidMat);
            liquidMesh.position.y = 1.45;
            bottleGroup.add(liquidMesh);

            // Gold Atomizer Collar & Nozzle
            const collarGeo = new THREE.CylinderGeometry(0.36, 0.36, 0.28, 32);
            const collarMesh = new THREE.Mesh(collarGeo, goldMetalMat);
            collarMesh.position.y = 3.08;
            bottleGroup.add(collarMesh);

            const nozzleBaseGeo = new THREE.CylinderGeometry(0.22, 0.24, 0.34, 32);
            sprayerHeadMesh = new THREE.Mesh(nozzleBaseGeo, goldMetalMat);
            sprayerHeadMesh.position.y = 3.36;

            // Tiny black pinhole on front of sprayer
            const holeGeo = new THREE.CylinderGeometry(0.04, 0.04, 0.05, 16);
            const holeMat = new THREE.MeshBasicMaterial({ color: 0x050505 });
            const holeMesh = new THREE.Mesh(holeGeo, holeMat);
            holeMesh.rotation.x = Math.PI / 2;
            holeMesh.position.set(0, 0.04, 0.21);
            sprayerHeadMesh.add(holeMesh);
            bottleGroup.add(sprayerHeadMesh);

            // Matte Black Rectangular Cap with Engraved 'V' on Top
            capGroup = new THREE.Group();
            capGroup.position.y = 3.62;
            bottleGroup.add(capGroup);

            const capTopTex = createCapTopVTexture();
            const capSideMat = new THREE.MeshStandardMaterial({
                color: 0x0d0d0d,
                roughness: 0.38,
                metalness: 0.15
            });
            const capTopMat = new THREE.MeshStandardMaterial({
                map: capTopTex,
                roughness: 0.32,
                metalness: 0.25
            });
            const capMaterials = [
                capSideMat, capSideMat, capTopMat, capSideMat, capSideMat, capSideMat
            ];
            const capGeo = new THREE.BoxGeometry(1.22, 0.88, 0.86);
            const capMesh = new THREE.Mesh(capGeo, capMaterials);
            capMesh.castShadow = true;
            capGroup.add(capMesh);

            // ==========================================
            // 3. LUXURY MATTE BLACK VELORA BOX (3D)
            // ==========================================
            boxGroup = new THREE.Group();
            boxGroup.position.set(-1.35, -1.9, -0.45);
            boxGroup.rotation.y = 0.22;
            podiumGroup.add(boxGroup);

            const boxFrontTex = createLuxuryBoxTexture();
            const boxSideMat = new THREE.MeshStandardMaterial({
                color: 0x0e0e0e,
                roughness: 0.55,
                metalness: 0.1
            });
            const boxFrontMat = new THREE.MeshStandardMaterial({
                map: boxFrontTex,
                roughness: 0.45,
                metalness: 0.18
            });
            const boxMaterials = [
                boxSideMat, boxSideMat, boxSideMat, boxSideMat, boxFrontMat, boxSideMat
            ];
            const boxGeo = new THREE.BoxGeometry(2.45, 3.85, 1.18);
            const boxMesh = new THREE.Mesh(boxGeo, boxMaterials);
            boxMesh.position.y = 1.925;
            boxMesh.castShadow = true;
            boxGroup.add(boxMesh);

            // ==========================================
            // 4. LUXURY 15ML TRAVEL ATOMIZER SPRAY (3D)
            // ==========================================
            travelAtomizerGroup = new THREE.Group();
            travelAtomizerGroup.position.set(2.55, -1.9, -0.25);
            travelAtomizerGroup.rotation.y = -0.35;
            podiumGroup.add(travelAtomizerGroup);

            const travelBodyGeo = new THREE.CylinderGeometry(0.32, 0.32, 1.85, 32);
            const travelBodyMat = new THREE.MeshStandardMaterial({
                color: 0x111111,
                roughness: 0.25,
                metalness: 0.45
            });
            const travelBodyMesh = new THREE.Mesh(travelBodyGeo, travelBodyMat);
            travelBodyMesh.position.y = 0.925;
            travelAtomizerGroup.add(travelBodyMesh);

            const travelGoldBandGeo = new THREE.CylinderGeometry(0.33, 0.33, 0.18, 32);
            const travelGoldBand = new THREE.Mesh(travelGoldBandGeo, goldMetalMat);
            travelGoldBand.position.y = 1.35;
            travelAtomizerGroup.add(travelGoldBand);

            // ==========================================
            // 5. FLOATING 3D PHOTO MONOLITHS (Displays User's Uploaded Images in 3D Space)
            // ==========================================
            photoMonolithGroup = new THREE.Group();
            photoMonolithGroup.visible = false;
            podiumGroup.add(photoMonolithGroup);
            update3DBackdropTextures();

            // Mouse & Touch Orbit Interaction Listeners
            let isDragging = false;
            let prevX = 0;
            let prevY = 0;

            container.addEventListener('mousedown', (e) => {
                isDragging = true;
                autoRotate3D = false;
                updateAutoRotateButtonUI();
                prevX = e.clientX;
                prevY = e.clientY;
            });

            window.addEventListener('mouseup', () => {
                isDragging = false;
            });

            window.addEventListener('mousemove', (e) => {
                if (!isDragging) return;
                const dx = e.clientX - prevX;
                const dy = e.clientY - prevY;
                prevX = e.clientX;
                prevY = e.clientY;

                targetTheta -= dx * 0.008;
                targetPhi = Math.max(0.45, Math.min(1.62, targetPhi - dy * 0.006));
            });

            // Touch Support for Mobile 3D Rotation
            container.addEventListener('touchstart', (e) => {
                if (e.touches.length === 1) {
                    isDragging = true;
                    autoRotate3D = false;
                    updateAutoRotateButtonUI();
                    prevX = e.touches[0].clientX;
                    prevY = e.touches[0].clientY;
                }
            }, { passive: true });

            container.addEventListener('touchend', () => {
                isDragging = false;
            });

            container.addEventListener('touchmove', (e) => {
                if (!isDragging || e.touches.length !== 1) return;
                const dx = e.touches[0].clientX - prevX;
                const dy = e.touches[0].clientY - prevY;
                prevX = e.touches[0].clientX;
                prevY = e.touches[0].clientY;

                targetTheta -= dx * 0.009;
                targetPhi = Math.max(0.45, Math.min(1.62, targetPhi - dy * 0.007));
            }, { passive: true });

            // Mouse Wheel Zoom inside 3D Viewport
            container.addEventListener('wheel', (e) => {
                e.preventDefault();
                targetRadius = Math.max(5.2, Math.min(13.5, targetRadius + e.deltaY * 0.004));
            }, { passive: false });

            window.addEventListener('resize', () => {
                if (!container || !renderer3D || !camera3D) return;
                const nw = container.clientWidth;
                const nh = container.clientHeight;
                camera3D.aspect = nw / nh;
                camera3D.updateProjectionMatrix();
                renderer3D.setSize(nw, nh);
            });

            animate3DStudio();
        }

        // Build/Update 3D Floating Gallery Slabs using current images
        function update3DBackdropTextures() {
            if (!photoMonolithGroup || typeof THREE === 'undefined') return;
            while (photoMonolithGroup.children.length > 0) {
                photoMonolithGroup.remove(photoMonolithGroup.children[0]);
            }

            const loader = new THREE.TextureLoader();
            const keys = ['hero', 'grid9', 'grid6'];
            const positions = [
                { x: -2.5, y: 0.4, z: -1.6, ry: 0.42 },
                { x: 0,    y: 0.6, z: -2.2, ry: 0 },
                { x: 2.5,  y: 0.4, z: -1.6, ry: -0.42 }
            ];

            keys.forEach((k, idx) => {
                loader.load(imageSources[k], (tex) => {
                    const geo = new THREE.BoxGeometry(2.1, 2.8, 0.08);
                    const frameMat = new THREE.MeshStandardMaterial({ color: 0xd4af37, metalness: 0.8, roughness: 0.2 });
                    const picMat = new THREE.MeshBasicMaterial({ map: tex });
                    const slab = new THREE.Mesh(geo, [frameMat, frameMat, frameMat, frameMat, picMat, frameMat]);
                    slab.position.set(positions[idx].x, positions[idx].y, positions[idx].z);
                    slab.rotation.y = positions[idx].ry;
                    photoMonolithGroup.add(slab);
                });
            });
        }

        // 3D Animation Loop
        function animate3DStudio() {
            requestAnimationFrame(animate3DStudio);
            if (!renderer3D || !scene3D || !camera3D) return;

            if (autoRotate3D) {
                targetTheta += 0.0045;
            }

            // Smooth interpolation for camera orbit
            camTheta += (targetTheta - camTheta) * 0.08;
            camPhi += (targetPhi - camPhi) * 0.08;
            camRadius += (targetRadius - camRadius) * 0.08;
            camLookY += (targetLookY - camLookY) * 0.08;

            camera3D.position.x = camRadius * Math.sin(camPhi) * Math.sin(camTheta);
            camera3D.position.y = camRadius * Math.cos(camPhi) + camLookY;
            camera3D.position.z = camRadius * Math.sin(camPhi) * Math.cos(camTheta);
            camera3D.lookAt(0, camLookY, 0);

            // Smooth Cap & Exploded View Animations
            if (capGroup && liquidMesh && sprayerHeadMesh) {
                const targetCapY = isExploded ? 4.95 : (isCapOpen ? 4.65 : 3.62);
                const targetCapRotY = (isCapOpen || isExploded) ? 0.55 : 0;
                capGroup.position.y += (targetCapY - capGroup.position.y) * 0.09;
                capGroup.rotation.y += (targetCapRotY - capGroup.rotation.y) * 0.09;

                const targetLiquidZ = isExploded ? 1.55 : 0;
                liquidMesh.position.z += (targetLiquidZ - liquidMesh.position.z) * 0.08;

                const targetBoxX = isExploded ? -2.25 : -1.35;
                if (boxGroup) boxGroup.position.x += (targetBoxX - boxGroup.position.x) * 0.08;
            }

            // Update 3D Volumetric Spray Particles
            for (let i = sprayParticles3D.length - 1; i >= 0; i--) {
                const sp = sprayParticles3D[i];
                sp.mesh.position.add(sp.vel);
                sp.mesh.scale.multiplyScalar(1.03);
                sp.mesh.material.opacity -= 0.018;
                if (sp.mesh.material.opacity <= 0) {
                    scene3D.remove(sp.mesh);
                    sprayParticles3D.splice(i, 1);
                }
            }

            renderer3D.render(scene3D, camera3D);
        }

        // Interactive 3D Controls
        function toggle3DCap() {
            isCapOpen = !isCapOpen;
            if (!isCapOpen) isExploded = false;
            const titleEl = document.getElementById('capToggleTitle');
            titleEl.textContent = isCapOpen ? 'إغلاق الغطاء الأسود (V)' : 'فتح الغطاء الأسود (V)';
            document.getElementById('studio3DInfoText').innerHTML = isCapOpen
                ? 'تم رفع الغطاء الأسود المحفور بحرف <strong class="text-gold">V</strong> ليكشف عن فوهة البخاخ الذهبية المصقولة.'
                : 'تم إغلاق الغطاء بإحكام فوق طوق البخاخ الذهبي.';
        }

        function trigger3DSpray() {
            if (!isCapOpen) {
                isCapOpen = true;
                document.getElementById('capToggleTitle').textContent = 'إغلاق الغطاء الأسود (V)';
            }
            triggerPerfumeSpray('gold');

            // Spawn 3D Mist Particles from the Gold Nozzle in WebGL space
            if (!scene3D || !bottleGroup) return;
            const worldNozzlePos = new THREE.Vector3(0.85, 1.5, 0.55);

            for (let i = 0; i < 42; i++) {
                const pGeo = new THREE.SphereGeometry(Math.random() * 0.09 + 0.03, 8, 8);
                const pMat = new THREE.MeshBasicMaterial({
                    color: i % 2 === 0 ? 0xf3e5ab : 0xd4af37,
                    transparent: true,
                    opacity: 0.75
                });
                const pMesh = new THREE.Mesh(pGeo, pMat);
                pMesh.position.copy(worldNozzlePos);

                const vel = new THREE.Vector3(
                    (Math.random() - 0.5) * 0.09,
                    Math.random() * 0.06 + 0.01,
                    Math.random() * 0.14 + 0.04
                );
                scene3D.add(pMesh);
                sprayParticles3D.push({ mesh: pMesh, vel });
            }
            document.getElementById('studio3DInfoText').innerHTML =
                'تم ضغط البخاخ الذهبي وإطلاق سحابة عطر <strong class="text-gold">VELORA Eau De Parfum</strong> في الفضاء ثلاثي الأبعاد!';
        }

        function toggle3DExplodedView() {
            isExploded = !isExploded;
            if (isExploded) isCapOpen = true;
            document.getElementById('explodeToggleTitle').textContent = isExploded
                ? 'إعادة تجميع الزجاجة (Normal 3D)'
                : 'العرض التفكيكي (Exploded 3D)';
            document.getElementById('studio3DInfoText').innerHTML = isExploded
                ? '<strong>وضع التفكيك الهندسي:</strong> يعرض الغطاء المحفور بحرف V، البخاخ الذهبي، الزجاج الخارجي، والقلب الكهرماني العطري بشكل منفصل.'
                : 'تمت إعادة تجميع كافة أجزاء الزجاجة ثلاثية الأبعاد.';
        }

        function cycle3DProductMode() {
            productLineupMode = (productLineupMode + 1) % 3;
            const titleEl = document.getElementById('lineupToggleTitle');
            const labelEl = document.getElementById('current3DModelLabel');

            if (productLineupMode === 0) {
                boxGroup.visible = true;
                travelAtomizerGroup.visible = true;
                photoMonolithGroup.visible = false;
                bottleGroup.position.set(0.85, -1.9, 0.35);
                titleEl.textContent = 'المجموعة الكاملة (الزجاجة + العلبة + البخاخ)';
                labelEl.textContent = 'VELORA 100ML + LUXURY BOX + TRAVEL ATOMIZER';
            } else if (productLineupMode === 1) {
                boxGroup.visible = false;
                travelAtomizerGroup.visible = false;
                photoMonolithGroup.visible = false;
                bottleGroup.position.set(0, -1.9, 0);
                titleEl.textContent = 'الزجاجة الرسمية منفردة (Solo 100ML)';
                labelEl.textContent = 'VELORA FLACON 100ML — SOLO EDITION';
            } else {
                boxGroup.visible = false;
                travelAtomizerGroup.visible = false;
                photoMonolithGroup.visible = true;
                bottleGroup.position.set(0, -1.9, 0.6);
                titleEl.textContent = 'الزجاجة 3D مع ألواح صورك الفوتوغرافية';
                labelEl.textContent = 'VELORA 3D + FLOATING PHOTOGRAPHY MONOLITHS';
            }
        }

        function set3DCameraPreset(preset) {
            autoRotate3D = false;
            updateAutoRotateButtonUI();
            if (preset === 'front') {
                targetTheta = 0;
                targetPhi = 1.42;
                targetRadius = 8.6;
                targetLookY = 0.5;
            } else if (preset === 'topV') {
                targetTheta = 0.2;
                targetPhi = 0.52;
                targetRadius = 6.5;
                targetLookY = 1.4;
            } else if (preset === 'side') {
                targetTheta = 1.25;
                targetPhi = 1.35;
                targetRadius = 8.8;
                targetLookY = 0.5;
            } else if (preset === 'macro') {
                targetTheta = 0.18;
                targetPhi = 1.28;
                targetRadius = 5.5;
                targetLookY = 1.1;
            }
        }

        function reset3DCamera() {
            targetTheta = 0.35;
            targetPhi = 1.32;
            targetRadius = 9.2;
            targetLookY = 0.6;
            autoRotate3D = true;
            updateAutoRotateButtonUI();
        }

        function toggle3DAutoRotate() {
            autoRotate3D = !autoRotate3D;
            updateAutoRotateButtonUI();
        }

        function updateAutoRotateButtonUI() {
            const txt = document.getElementById('autoRotateText');
            if (txt) txt.textContent = autoRotate3D ? 'الدوران التلقائي: مفعل' : 'الدوران التلقائي: متوقف';
        }

        function set3DLightingMood(mood, btnEl) {
            document.querySelectorAll('.studio-light-btn').forEach(b => {
                b.className = 'studio-light-btn px-3.5 py-2 rounded-xl bg-white/5 text-stone-300 hover:bg-white/10 border border-white/10 text-xs transition';
            });
            btnEl.className = 'studio-light-btn px-3.5 py-2 rounded-xl bg-gold text-obsidian font-bold text-xs transition';

            if (!pointLightGold || !pointLightAmber || !spotLightMain) return;
            if (mood === 'gold') {
                pointLightGold.color.setHex(0xd4af37);
                pointLightAmber.color.setHex(0xc87a28);
                spotLightMain.intensity = 2.2;
            } else if (mood === 'obsidian') {
                pointLightGold.color.setHex(0x7098c4);
                pointLightAmber.color.setHex(0xd4af37);
                spotLightMain.intensity = 1.5;
            } else if (mood === 'sunset') {
                pointLightGold.color.setHex(0xff6b2b);
                pointLightAmber.color.setHex(0xffaa33);
                spotLightMain.intensity = 2.6;
            }
        }

        window.onload = function() {
            preloadGridImage('grid9');
            preloadGridImage('grid6');
            renderSlicedGallery();
            animateAromaLoop();
            initVelora3DStudio();
        };
    </script>
</body>
</html>
```
