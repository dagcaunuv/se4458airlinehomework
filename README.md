https://github.com/dagcaunuv/se4458airlinehomework.git 

https://airlineapi20241128165626.azurewebsites.net/swagger/index.html


https://drive.google.com/file/d/10s8PN9xSSK7QbLplbmTMlL-W-ev2sDzI/view?usp=drive_link




-------------------------------------------------------------------------------------------------

Uygulamanın Tasarımı:

Katmanlar:

API Katmanı:
Kullanıcılarla etkileşim kurar.
HTTP isteklerini işler ve ilgili servis çağrılarını yapar.
Servis Katmanı:
İş mantığını kapsar.
Veritabanıyla ilgili işlemler ve API ile iş mantığı arasındaki iletişim bu katmanda gerçekleştirilir.
UserService sınıfı, kullanıcı doğrulama, kayıt ve token üretme işlemlerini yönetir.
Veri Erişim Katmanı:
Veritabanı işlemleri gerçekleştirilir.
AirlineDbContext sınıfı, veritabanı işlemlerini yönetir ve Entity Framework Core ile çalışır.
Model Katmanı:
DTO'lar ve veri modelleri, uygulamada kullanılan veri yapılarını temsil eder.
Veri Modelleri:

Kullanıcı Modeli (User):
Veritabanındaki kullanıcı tablosunu temsil eder. Örnek alanlar: UserId, UserName, Name, Password, Role.
DTO Modelleri:
LoginRequestDTO: Giriş işlemi için gerekli bilgileri taşır (UserName, Password).
RegisterRequestDTO: Kullanıcı kaydı için gerekli bilgileri taşır (UserName, Password, Name, Role).
LoginResponseDTO: Giriş işlemine yanıt olarak dönen veriyi içerir (Token, APIUser).
JWT (JSON Web Token):

Kullanıcı doğrulama işlemi için JWT kullanılmıştır.
Token, kullanıcı adı ve rol bilgilerini içeren bir JWT ile üretilir.
HMAC-SHA256 algoritması ile imzalanır.
Konfigürasyon:

appsettings.json:
Veritabanı bağlantı bilgilerini (ConnectionStrings) içerir.
Token üretiminde kullanılan gizli anahtar (ApiSettings:Secret) saklanır.
Varsayımlar:

Kimlik Doğrulama: Kullanıcıların yalnızca UserName ve Password ile doğrulandığı varsayılmıştır. Daha güvenli bir sistem için parolaların hashlenmesi (örn. BCrypt) önerilirToken Geçerlilik Süresi: Token'lerin yalnızca 15 dakika geçerli olduğu varsayılmıştır. Ancak token yenileme mekanizması eklenmemiştir..

Roller: Kullanıcıların sistemde farklı roller (Role) olduğu varsayılmıştır (örn. Admin, User). Yetkilendirme bu rollere dayanarak yapılır.    



Şifre Güvenliği: Şifrelerin açık metin olarak saklandığı görülmektedir. Güvenlik açısından şifrelerin hashlenmesi gereklidir.

Bağlantı Güvenliği: Veritabanı bağlantısı için bir SQL Azure sunucusu kullanılmış ve bağlantının şifreli olduğu (SSL) varsayılmıştır.

Gizli Anahtar: JWT için kullanılan gizli anahtar appsettings.json içinde saklanmıştır. Daha güvenli bir yöntem olarak, çevresel değişkenler veya gizli yapılandırma servisleri (örn. Azure Key Vault) tercih edilebilir.
----------------------------------------------------------------------------------------------------
