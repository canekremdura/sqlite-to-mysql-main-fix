# SQLite to MySQL Dönüştürücü

SQLite veritabanlarını MySQL uyumlu SQL formatına dönüştürmek için geliştirilmiş Python tabanlı araç.

## Geliştirme Geçmişi

Bu proje başlangıçta SQLite veritabanlarını MySQL'e dönüştürme yeteneğine sahipti ancak bazı veri türü uyumluluk sorunları içeriyordu. Bu sorunlar tespit edilip çözülmüştür.

## Fixlenen Sorunlar

### 1. Varchar Uzunluğu Sorunu
**Sorun:** SQLite'de `varchar` alanlar uzunluk belirtmeden tanımlanabiliyor, ancak MySQL bu durumda syntax hatası veriyor.

**Örnek Hatalı Tanım:**
```sql
CREATE TABLE `migrations` (`migration` varchar NOT NULL, `batch` INT NOT NULL)
```

**MySQL Hatası:**
```
#1064 - You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'NOT NULL, `batch` INT NOT NULL) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE...' at line 2
```

**Çözüm:** Tüm `varchar` alanlara `varchar(255)` gibi uzunluk belirtildi.

### 2. Numeric Veri Türü Uyumsuzluğu
**Sorun:** SQLite'de `numeric` veri türleri doğrudan MySQL'e aktarılınca uyumsuzluk oluşabiliyor.

**Çözüm:** `numeric` veri türleri uygun `decimal(10,2)` formata dönüştürüldü.

## Uygulanan Düzeltmeler

Düzeltmeler doğrudan `sqlite_to_mysql_type` fonksiyonuna entegre edilmiştir ve şu dönüşümleri içerir:

- `varchar` türlerine otomatik olarak `varchar(255)` gibi uzunluk eklenir
- `numeric` türleri `decimal(10,2)` formatına dönüştürülür
- `char`, `varbinary`, `binary` gibi türler için de varsayılan uzunluklar tanımlanmıştır

## Özellikler

- SQLite veritabanı dosyalarını MySQL uyumlu SQL dump dosyalarına dönüştürme
- Tüm tablo yapılarını ve verileri koruma
- MySQL uyumlu veri türü dönüştürme
- Ctrl+C ile kesintiye uğramış işlemleri zarif sonlandırma
- UTF-8 karakter kodlaması desteği

## Gereksinimler

- Python 3.x
- SQLite veritabanı dosyası
- MySQL (dönüştürülen dosyayı içe aktarmak için)

## Kullanım

1. Proje klasörüne gidin
2. SQLite dosyanızı dönüştürmek için aşağıdaki komutu çalıştırın:

```
python export.py <sqlite_db_file> [mysql_dump_file]
```

Örnek:
```
python export.py veritabani.sqlite cikti.sql
```

## Geliştirici Bilgisi

**Orijinal Geliştirici:** Majid Alavizadeh 
**Düzeltmeler ve Geliştirmeler:** Can Ekrem Dura

## Lisans

Bu proje MIT Lisansı ile lisanslanmıştır.