# KutuphaneOtomasyonu
Bu proje, bir kütüphane yönetim sistemini uygulayan bir C# konsol uygulamasıdır. Temel amacı, kütüphanedeki kitap ve üye bilgilerini düzenleyebilmek ve kütüphane işlemlerini yönetebilmektir. 
Kullanıcılar, kitapları ekleyebilir, silebilir, üyeleri ekleyebilir, silebilir, kitapları üyelere verebilir, geri alabilir, kitaplara yorum ekleyebilir ve silebilir, üyelerin aldığı kitapları listeleyebilir. Programın akışı, kullanıcıların giriş yapmasıyla başlar. Giriş yaptıktan sonra, kullanıcılar çeşitli işlemleri seçebilirler. Yeni kitap ekleyebilir, kitapları silebilir, üye ekleyebilir, üyeleri silebilir, kitapları listeleyebilir, üyeleri listeleyebilir, kitapları ödünç alabilir, geri verebilir, kitaplara yorum ekleyebilir, yorum silebilir ve kitap yorumlarını listeleyebilirler. 
Sınıflar:
Kullanici (Kullanıcı):
Özellikleri: KullaniciAdi (Kullanıcı Adı), Sifre (Şifre).
Kitap (Kitap):
Özellikleri: KitapAdi (Kitap Adı), Yazar (Yazar), Yayınevi (Yayıncı), Sayfa Sayısı (Sayfa Sayısı), YayinTarihi (Yayın Tarihi), UyeId (Üye Kimliği), KitapKodu (Kitap Kodu), Yorum (Yorum).
Uye (Üye):
Özellikleri: Ad (Ad), Soyad (Soyadı), Telefon (Telefon), Email, UyeId (Üye Kimliği), Kitaplar (Kitap Listesi).
KitapUye (KitapÜyesi):
Özellikleri: UyeId (Üye ID), KitapKodu (Kitap Kodu).
Kutuphane (Kütüphane):
Özellikleri: Kitaplar (Kitap listesi), Uyeler (Üye listesi).
Yöntemler: KitapKaydet (Kitap Kaydet), KitapSil (Kitap Sil), KitaplariListele (Kitap Listele), UyeKaydet (Üye Kaydet), UyeSil (Üye Sil), UyeleriListele (Üyeleri Listele), KitapAl (Kitap Ödünç Al), KitapIade (Kitap İade), UyeninAldigiKitaplariListele (Üyenin Ödünç Aldığı Kitapları Listele), KitapYorumuEkle (Kitap Yorumu Ekle), KitapYorumuSil (Kitap Yorumunu Sil), KitapYorumlariniListele (Kitap Yorumlarını Listele).
Program:
Ana yöntem: Uygulamanın ana giriş noktası.
Kullanıcı girişini yönetir ve seçilen seçeneğe göre kitaplık yönetimi işlemlerini yürütür.
Programın Akışı:
Kullanıcılardan (yöneticilerden) bir kullanıcı adı ve şifreyle giriş yapmaları istenir.
Giriş yaptıktan sonra kütüphanedeki kitaplar ve üyeler üzerinde kitap veya üye ekleme/silme, kitap veya üye listeleme, kitap ödünç alma/iade etme, kitap yorumu ekleme/silme, kitap yorumlarını listeleme gibi çeşitli işlemleri gerçekleştirebilirler.
Program, kullanıcılardan çıkmayı seçinceye kadar sürekli olarak giriş yapmalarını istemek için bir while döngüsü kullanır (seçenek 0).
GetHiddenInput yöntemini kullanarak şifre girişini gizlemek için basit bir mekanizma vardır.
Kod, giriş/çıkış işlemleri için Konsolu kullanır.
Veriler (kitaplar, üyeler) Kutuphane sınıfı içindeki listelerde saklanır.
