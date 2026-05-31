<!DOCTYPE html>  
<html lang="ru">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>ЛапкиЗдоровье — Ветклиника для кошек и собак</title>  
    <script src="https://cdn.tailwindcss.com"></script>  
    <script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js"></script>  
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">  
    <style>  
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Playfair+Display:wght@700&display=swap');  
          
        body { font-family: 'Inter', sans-serif; }  
        .logo { font-family: 'Playfair Display', serif; }  
  
        .glass {   
            background: rgba(255,255,255,0.13);   
            backdrop-filter: blur(20px);   
            border: 1px solid rgba(255,255,255,0.25);   
        }  
          
        .modal {  
            animation: modalPop 0.5s ease-out;  
        }  
        @keyframes modalPop {  
            from { transform: scale(0.7); opacity: 0; }  
            to { transform: scale(1); opacity: 1; }  
        }  
  
        .side-menu {  
            transform: translateX(120%);  
            transition: transform 0.6s ease;  
        }  
        .side-menu.open {  
            transform: translateX(0);  
        }  
    </style>  
</head>  
<body class="bg-gradient-to-br from-orange-950 via-amber-900 to-orange-950 text-white min-h-screen">  
  
    <!-- Шапка -->  
    <header class="fixed w-full z-50">  
        <nav class="max-w-6xl mx-auto px-6 py-5 glass rounded-b-3xl m-3 flex items-center justify-between">  
            <div class="w-10"></div>  
            <div class="logo text-4xl font-bold flex items-center gap-3">  
                <span class="text-orange-400">🐾</span> ЛапкиЗдоровье <span class="text-orange-400">🐾</span>  
            </div>  
            <button onclick="toggleMenu()" class="text-4xl hover:scale-110 transition">☰</button>  
        </nav>  
    </header>  
  
    <!-- Главный экран -->  
    <section class="min-h-screen flex items-center justify-center text-center relative">  
        <div class="absolute inset-0 bg-black/50"></div>  
        <div class="relative max-w-3xl px-6 pt-20">  
            <h1 class="text-6xl font-bold mb-6">ЛапкиЗдоровье</h1>  
            <p class="text-2xl mb-8">Ветеринарная клиника для кошек и собак в Чикаго</p>  
            <p class="text-lg max-w-2xl mx-auto opacity-90 mb-12">  
                Профессиональная забота, современное оборудование и любовь к вашим питомцам.  
            </p>  
            <button onclick="openAppointmentModal()"   
                    class="bg-white text-orange-700 px-12 py-5 rounded-3xl text-xl font-semibold hover:scale-105 transition">  
                Записаться на приём  
            </button>  
        </div>  
    </section>  
  
    <!-- Боковое меню -->  
    <div id="sideMenu" class="side-menu fixed top-0 right-0 h-full w-80 glass shadow-2xl z-50 p-8">  
        <button onclick="toggleMenu()" class="text-4xl absolute top-6 right-6">✕</button>  
        <div class="mt-20 space-y-4 text-lg">  
            <a onclick="showServiceModal('vaccine')" class="block py-4 px-6 hover:bg-white/10 rounded-2xl transition">💉 Вакцинация</a>  
            <a onclick="showServiceModal('surgery')" class="block py-4 px-6 hover:bg-white/10 rounded-2xl transition">🔪 Стерилизация</a>  
            <a onclick="showServiceModal('diagnostics')" class="block py-4 px-6 hover:bg-white/10 rounded-2xl transition">🩻 Диагностика</a>  
            <a onclick="showServiceModal('dental')" class="block py-4 px-6 hover:bg-white/10 rounded-2xl transition">🦷 Стоматология</a>  
            <a href="upload.html" class="block py-4 px-6 hover:bg-white/10 rounded-2xl transition">📸 Загрузить фото</a>  
        </div>  
    </div>  
  
    <!-- Модальное окно записи -->  
    <div id="appointmentModal" class="hidden fixed inset-0 bg-black/70 flex items-center justify-center z-[100]">  
        <div class="modal glass max-w-lg w-full mx-4 rounded-3xl p-8">  
            <button onclick="closeAppointmentModal()" class="absolute top-4 right-4 text-3xl">✕</button>  
            <h2 class="text-3xl font-bold text-center mb-8">Запись на приём</h2>  
              
            <form id="appointmentForm" class="space-y-5">  
                <input type="text" id="ownerName" placeholder="Имя владельца" class="w-full p-4 rounded-2xl bg-white/10 border border-white/30 focus:border-orange-400" required>  
                <input type="text" id="petName" placeholder="Кличка питомца" class="w-full p-4 rounded-2xl bg-white/10 border border-white/30 focus:border-orange-400" required>  
                <select id="petType" class="w-full p-4 rounded-2xl bg-white/10 border border-white/30 focus:border-orange-400">  
                    <option>Кошка</option>  
                    <option>Собака</option>  
                </select>  
                <input type="tel" value="+7 901 856-92-59" class="w-full p-4 rounded-2xl bg-white/10 border border-white/30 focus:border-orange-400" required>  
                <input type="date" id="date" class="w-full p-4 rounded-2xl bg-white/10 border border-white/30 focus:border-orange-400" required>  
                <textarea id="problem" placeholder="Опишите проблему" rows="4" class="w-full p-4 rounded-2xl bg-white/10 border border-white/30 focus:border-orange-400"></textarea>  
                  
                <button type="submit" class="w-full bg-gradient-to-r from-orange-500 to-amber-500 py-6 rounded-3xl text-xl font-semibold">  
                    Отправить заявку  
                </button>  
            </form>  
        </div>  
    </div>  
  
    <!-- Окно благодарности -->  
    <div id="thankModal" class="hidden fixed inset-0 bg-black/70 flex items-center justify-center z-[110]">  
        <div class="modal glass max-w-md w-full mx-4 rounded-3xl p-10 text-center">  
            <div class="text-7xl mb-6">🐾</div>  
            <h2 class="text-3xl font-bold mb-4">Спасибо!</h2>  
            <p class="text-lg">Мы свяжемся с вами по номеру <strong>+7 901 856-92-59</strong> в ближайшее время ❤️</p>  
            <button onclick="closeThankModal()" class="mt-8 bg-white text-orange-700 px-10 py-4 rounded-3xl font-semibold">Закрыть</button>  
        </div>  
    </div>  
  
    <footer class="py-12 text-center glass">  
        <p class="text-2xl font-bold mb-3">ЛапкиЗдоровье</p>  
        <p>📞 <a href="tel:+79018569259">+7 901 856-92-59</a></p>  
        <p class="opacity-70">Чикаго, Иллинойс • 24/7</p>  
    </footer>  
  
    <script>  
        emailjs.init("zLcJTw6oGJxWwXS7t");  
  
        function toggleMenu() {  
            document.getElementById('sideMenu').classList.toggle('open');  
        }  
  
        function openAppointmentModal() {  
            document.getElementById('appointmentModal').classList.remove('hidden');  
        }  
  
        function closeAppointmentModal() {  
            document.getElementById('appointmentModal').classList.add('hidden');  
        }  
  
        function closeThankModal() {  
            document.getElementById('thankModal').classList.add('hidden');  
        }  
  
        function showServiceModal(type) {  
            toggleMenu();  
            setTimeout(() => alert("Описание услуги скоро будет добавлено."), 400);  
        }  
  
        document.getElementById('appointmentForm').addEventListener('submit', function(e) {  
            e.preventDefault();  
  
            const formData = {  
                ownerName: document.getElementById('ownerName').value,  
                petName: document.getElementById('petName').value,  
                petType: document.getElementById('petType').value,  
                phone: "+7 901 856-92-59",  
                date: document.getElementById('date').value,  
                problem: document.getElementById('problem').value || "Не указано"  
            };  
  
            emailjs.send("service_p06s572", "template_zs9auie", formData)  
                .then(() => {  
                    closeAppointmentModal();  
                    document.getElementById('thankModal').classList.remove('hidden');  
                    e.target.reset();  
                })  
                .catch(() => alert("Ошибка отправки. Проверьте интернет."));  
        });  
    </script>  
</body>  
</html>  
