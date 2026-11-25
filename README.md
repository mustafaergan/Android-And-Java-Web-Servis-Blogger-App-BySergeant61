# Android Blog Uygulaması ve Java Web Servisi

Konu başlıkları açıp altında mesajlaşılan basit bir blog/forum uygulaması: Android istemci ve onun konuştuğu Jersey + Hibernate REST servisi. Java/Android eğitimi sırasında örnek proje olarak yazıldı.

> **Not:** Bu depo 2017 yılında eğitim/örnek amaçlı yazıldı ve artık güncellenmiyor. Bağımlılıkları eskidir ve bilinen güvenlik açıkları içerir; üretimde kullanmayın.

## İçerik

| Klasör | Ne yapar |
|---|---|
| `Bloger` | Android uygulaması. Giriş ekranı (`MainActivity`), konu başlıkları listesi (`BasliklarActivity`), konu ekleme, bir başlık altındaki mesajlar (`ChatActivity`), kullanıcı ekleme ve listeleme. Servisle Volley + Gson üzerinden JSON alışverişi yapar. |
| `Blog Web Servis` | Jersey 1.x REST servisi (`/rest/servis/...`). Kullanıcı, rol, başlık ve mesaj kayıtları için ekleme/silme/listeleme uçları; veritabanı erişimi Hibernate ile `DAO` sınıfında. `soket` paketinde ayrıca basit bir TCP sohbet sunucusu/istemcisi denemesi vardır. |

## Teknolojiler

- Android: compileSdk 25 (minSdk 11), Android Gradle Plugin 2.3.3, Gradle 3.3, Volley 1.0.19, Gson 2.8.0, AppCompat/RecyclerView 25.3.1, yerel jar olarak EasyAndroidAnimations 0.5
- Servis: Java 8, Maven (`war`), Jersey 1.8, Hibernate 5.1, MySQL Connector 5.1

## Çalıştırma

1. **Servis:** `Blog Web Servis` klasörünü Eclipse'e Maven projesi olarak alıp bir Tomcat sunucusunda çalıştırın ya da `mvn package` ile `war` üretin. MySQL'de `blog` adlı bir veritabanı oluşturun; bağlantı bilgileri `Blog Web Servis/src/main/resources/hibernate.cfg.xml` içindedir, kendi kullanıcı adı ve şifrenizi yazın (tablolar `hbm2ddl.auto=update` ile oluşur).
2. **Android:** `Bloger` klasörünü Android Studio ile açın. Servisin adresi `app/src/main/res/values/strings.xml` içindeki `ipPort` değerinden okunur; kendi sunucunuzun adresine göre değiştirin.
3. Uygulamayı emülatörde ya da cihazda çalıştırın.
