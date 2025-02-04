# Laravel 11 Docker Projesi

Bu proje, Laravel 11 framework'ü kullanılarak Docker üzerinde çalışan bir web uygulamasıdır. Proje içerisinde PostgreSQL veritabanı ve Redis önbellek sistemi bulunmaktadır.

## 🚀 Teknolojiler

- Laravel 11
- PHP 8.2
- PostgreSQL 15
- Redis (Alpine)
- Nginx
- Docker & Docker Compose

## 📋 Gereksinimler

- Docker
- Docker Compose

## 🛠️ Kurulum

1. Projeyi klonlayın:
```bash
git clone <repository-url>
cd laravel-docker-project
```

2. Gerekli .env dosyalarını oluşturun:
```bash
# Laravel .env dosyası
cp backend/.env.example backend/.env

# Docker .env dosyası
cp .env.example .env
```

3. Laravel `.env` dosyasında aşağıdaki değişkenleri ayarlayın:
```env
DB_CONNECTION=pgsql
DB_HOST=db
DB_PORT=5432
DB_DATABASE=backend
DB_USERNAME=your_username
DB_PASSWORD=your_password

REDIS_HOST=redis
REDIS_PASSWORD=your_redis_password
REDIS_PORT=6379
```

4. Ana dizindeki `.env` dosyasında Docker servisleri için gerekli değişkenleri ayarlayın:
```env
DB_DATABASE=backend
DB_USERNAME=your_username
DB_PASSWORD=your_password
REDIS_PASSWORD=your_redis_password
```

5. Docker konteynerlerini başlatın:
```bash
docker compose build
docker compose up -d
```

6. Composer bağımlılıklarını yükleyin:
```bash
docker compose exec app composer install
```

7. Laravel migration'ları çalıştırın:
```bash
docker compose exec app php artisan migrate
```

## 🌐 Kullanım

Uygulama http://localhost:8000 adresinde çalışacaktır.

Mevcut rotalar:
- `/`: Ana sayfa
- `/test`: Test sayfası

## 📁 Proje Yapısı

```
laravel-docker-project/
├── backend/             # Laravel uygulaması
├── nginx/              # Nginx konfigürasyonu
│   └── conf.d/
├── .env                # Docker environment değişkenleri
├── docker-compose.yml  # Docker compose konfigürasyonu
└── README.md
```

## 🐳 Docker Konteynerler

- **app**: Laravel uygulaması (PHP-FPM)
- **nginx**: Web sunucusu
- **db**: PostgreSQL veritabanı
- **redis**: Redis önbellek sunucusu

## 🤝 Katkıda Bulunma

1. Fork edin
2. Feature branch oluşturun (`git checkout -b feature/amazing-feature`)
3. Değişikliklerinizi commit edin (`git commit -m 'feat: Add amazing feature'`)
4. Branch'inizi push edin (`git push origin feature/amazing-feature`)
5. Pull Request oluşturun

## 📝 Lisans

Bu proje MIT lisansı altında lisanslanmıştır. Daha fazla bilgi için `LICENSE` dosyasına bakın.
