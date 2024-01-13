using System;
using System.Collections.Generic;

public class Kullanici
{
    public string KullaniciAdi { get; set; }
    public string Sifre { get; set; }
}

public class Kitap
{
    public string KitapAdi { get; set; }
    public string Yazar { get; set; }
    public string Yayinevi { get; set; }
    public int SayfaSayisi { get; set; }
    public int YayinTarihi { get; set; }
    public int UyeId { get; set; }
    public int KitapKodu { get; set; }
    public string Yorum { get; set; }
}

public class Uye
{
    public string Ad { get; set; }
    public string Soyad { get; set; }
    public string Telefon { get; set; }
    public string Email { get; set; }
    public int UyeId { get; set; }
    public List<Kitap> Kitaplar { get; set; }
}

public class KitapUye
{
    public int UyeId { get; set; }
    public int KitapKodu { get; set; }
}

public class Kutuphane
{
    public List<Kitap> Kitaplar { get; set; }
    public List<Uye> Uyeler { get; set; }

    public Kutuphane()
    {
        Kitaplar = new List<Kitap>();
        Uyeler = new List<Uye>();
    }

    public void KitapKaydet(string ad, string yazar, string yayinevi, int sayfaSayisi, int yayinTarihi, int kitapKodu)
    {
        Kitap kitap = new Kitap
        {
            KitapAdi = ad,
            Yazar = yazar,
            Yayinevi = yayinevi,
            SayfaSayisi = sayfaSayisi,
            YayinTarihi = yayinTarihi,
            KitapKodu = kitapKodu,
            UyeId = 0
        };
        Kitaplar.Add(kitap);
        Console.WriteLine("Kitap kaydedildi: " + kitap.KitapAdi);
        Console.WriteLine();
    }

    public void KitapSil(int kitapKodu)
    {
        Kitap silinecekKitap = Kitaplar.Find(kitap => kitap.KitapKodu == kitapKodu);
        if (silinecekKitap != null)
        {
            Kitaplar.Remove(silinecekKitap);
            Console.WriteLine("Kitap silindi: " + silinecekKitap.KitapAdi);
            Console.WriteLine();
        }
        else
        {
            Console.WriteLine("Kitap bulunamadı!");
            Console.WriteLine();
        }
    }

    public void KitaplariListele()
    {
        Console.WriteLine("Kitaplar:");
        foreach (Kitap kitap in Kitaplar)
        {
            Console.WriteLine("Kitap Adı: " + kitap.KitapAdi);
            Console.WriteLine("Yazar: " + kitap.Yazar);
            Console.WriteLine("Yayınevi: " + kitap.Yayinevi);
            Console.WriteLine("Sayfa Sayısı: " + kitap.SayfaSayisi);
            Console.WriteLine("Yayın Tarihi: " + kitap.YayinTarihi);
            Console.WriteLine("Kitap ID: " + kitap.KitapKodu);
            Console.WriteLine("-----------------------------");
        }
    }

    public void UyeKaydet(string ad, string soyad, string telefon, string email, int uyeId)
    {
        Uye uye = new Uye
        {
            Ad = ad,
            Soyad = soyad,
            Telefon = telefon,
            Email = email,
            UyeId = uyeId,
            Kitaplar = new List<Kitap>()
        };
        Uyeler.Add(uye);
        Console.WriteLine("Üye kaydedildi: " + uye.Ad + " " + uye.Soyad);
        Console.WriteLine();
    }

    public void UyeSil(int uyeId)
    {
        Uye silinecekUye = Uyeler.Find(uye => uye.UyeId == uyeId);
        if (silinecekUye != null)
        {
            Uyeler.Remove(silinecekUye);
            Console.WriteLine("Üye silindi: " + silinecekUye.Ad + " " + silinecekUye.Soyad);
            Console.WriteLine();
        }
        else
        {
            Console.WriteLine("Üye bulunamadı!");
            Console.WriteLine();
        }
    }

    public void UyeleriListele()
    {
        Console.WriteLine("Üyeler:");
        foreach (Uye uye in Uyeler)
        {
            Console.WriteLine("Ad: " + uye.Ad);
            Console.WriteLine("Soyad: " + uye.Soyad);
            Console.WriteLine("Telefon: " + uye.Telefon);
            Console.WriteLine("Email: " + uye.Email);
            Console.WriteLine("Üye ID: " + uye.UyeId);
            Console.WriteLine("-----------------------------");
        }
    }

    public void KitapAl(int uyeId, int kitapKodu)
    {
        Kitap kitap = Kitaplar.Find(k => k.UyeId == 0 && k.KitapKodu == kitapKodu);
        Uye uye = Uyeler.Find(u => u.UyeId == uyeId);

        if (kitap == null)
        {
            Console.WriteLine("Kitap bulunamadı veya zaten bir üye tarafından alınmış.");
            Console.WriteLine();
            return;
        }

        if (uye == null)
        {
            Console.WriteLine("Üye bulunamadı.");
            Console.WriteLine();
            return;
        }

        kitap.UyeId = uyeId;
        uye.Kitaplar.Add(kitap);

        Console.WriteLine("Kitap başarıyla alındı. " + uyeId + " ID numarasına sahip üye, " + kitapKodu + " kodlu kitabı almıştır.");
        Console.WriteLine();
    }

    public void KitapIade(int uyeId, int kitapKodu)
    {
        Uye uye = Uyeler.Find(u => u.UyeId == uyeId);

        if (uye != null && uye.Kitaplar != null)
        {
            Kitap kitap = uye.Kitaplar.Find(k => k.KitapKodu == kitapKodu);

            if (kitap != null)
            {
                kitap.UyeId = 0;
                uye.Kitaplar.Remove(kitap);

                Console.WriteLine($"Kitap iade edildi: {kitap.KitapAdi}");
                Console.WriteLine();
            }
            else
            {
                Console.WriteLine("Üyenin bu kitabı almamış olduğu veya kitap bulunamadı!");
                Console.WriteLine();
            }
        }
        else
        {
            Console.WriteLine("Üye bulunamadı veya üye hiç kitap almamış.");
            Console.WriteLine();
        }
    }

    public void UyeninAldigiKitaplariListele(int uyeId)
    {
        Uye uye = Uyeler.Find(u => u.UyeId == uyeId);

        if (uye != null && uye.Kitaplar != null && uye.Kitaplar.Count > 0)
        {
            Console.WriteLine($"{uye.Ad} {uye.Soyad}'ın Aldığı Kitaplar:");
            foreach (Kitap kitap in uye.Kitaplar)
            {
                Console.WriteLine($"Kitap Adı: {kitap.KitapAdi}");
                Console.WriteLine($"Yazar: {kitap.Yazar}");
                Console.WriteLine($"Yayınevi: {kitap.Yayinevi}");
                Console.WriteLine($"Sayfa Sayısı: {kitap.SayfaSayisi}");
                Console.WriteLine($"Yayın Tarihi: {kitap.YayinTarihi}");
                Console.WriteLine($"Kitap ID: {kitap.KitapKodu}");
                Console.WriteLine($"Yorum: {kitap.Yorum}");  // Yorumu listele
                Console.WriteLine("-----------------------------");
            }
        }
        else
        {
            Console.WriteLine("Üye bulunamadı veya üye hiç kitap almamış.");
        }

        Console.WriteLine();
    }

    public void KitapYorumuEkle(string kitapAdi, string yorum)
    {
        Kitap kitap = Kitaplar.Find(k => k.KitapAdi == kitapAdi);

        if (kitap != null)
        {
            kitap.Yorum = yorum;
            Console.WriteLine("Yorum eklendi:");
            Console.WriteLine("Kitap Adı: " + kitap.KitapAdi);
            Console.WriteLine("Yorum: " + kitap.Yorum);
        }
        else
        {
            Console.WriteLine("Kitap bulunamadı!");
        }
        Console.WriteLine();
    }

    public void KitapYorumuSil(string kitapAdi)
    {
        Kitap kitap = Kitaplar.Find(k => k.KitapAdi == kitapAdi);

        if (kitap != null)
        {
            kitap.Yorum = null;
            Console.WriteLine("Yorum silindi:");
            Console.WriteLine("Kitap Adı: " + kitap.KitapAdi);
        }
        else
        {
            Console.WriteLine("Kitap bulunamadı!");
        }
        Console.WriteLine();
    }

    public void KitapYorumlariniListele(string kitapAdi)
    {
        Kitap kitap = Kitaplar.Find(k => k.KitapAdi == kitapAdi);

        if (kitap != null)
        {
            Console.WriteLine($"Yorumlar Kitap Adı: {kitap.KitapAdi}");
            if (kitap.Yorum != null)
            {
                Console.WriteLine($"Yorum: {kitap.Yorum}");
            }
            else
            {
                Console.WriteLine("Henüz yorum eklenmemiş.");
            }
        }
        else
        {
            Console.WriteLine("Kitap bulunamadı!");
        }
        Console.WriteLine();
    }
}

public class Program
{
    private static Kullanici currentUser;
    private static Kullanici kullanici = new Kullanici
    {
        KullaniciAdi = "admin",
        Sifre = "şifre123"
    };

    public static void Main(string[] args)
    {
        Kutuphane kutuphane = new Kutuphane();

        while (true)
        {
            Console.WriteLine("Kütüphane Yönetim Sistemine Hoş Geldiniz!");

            if (currentUser == null)
            {
                Console.WriteLine("Lütfen giriş yapın:");

                Console.Write("Kullanıcı Adı: ");
                string kullaniciAdi = Console.ReadLine();

                Console.Write("Şifre: ");
                string sifre = GetHiddenInput();

                if (kullaniciAdi == kullanici.KullaniciAdi && sifre == kullanici.Sifre)
                {
                    currentUser = kullanici;
                    Console.WriteLine("Giriş başarılı!");
                }
                else
                {
                    Console.WriteLine("Geçersiz kullanıcı adı veya şifre!");
                    continue;
                }
            }

            Console.WriteLine("Yapmak istediğiniz işlemi seçin:");
            Console.WriteLine("1. Yeni kitap eklemek");
            Console.WriteLine("2. Kitap silme");
            Console.WriteLine("3. Yeni üye eklemek");
            Console.WriteLine("4. Üye silme");
            Console.WriteLine("5. Kitapları listelemek");
            Console.WriteLine("6. Üyeleri listelemek");
            Console.WriteLine("7. Kitapla üyeyi birleştirmek");
            Console.WriteLine("8. Hangi üye hangi kitabı almıştır?");
            Console.WriteLine("9. Kitap iadesi");
            Console.WriteLine("10. Kitap yorumu ekleme");
            Console.WriteLine("11. Kitap yorumu silme");
            Console.WriteLine("12. Kitap yorumlarını listeleme");
            Console.WriteLine("0. Çıkış");
            Console.WriteLine();

            int secim;
            if (!int.TryParse(Console.ReadLine(), out secim))
            {
                Console.WriteLine("Geçersiz seçim!");
                Console.WriteLine();
                continue;
            }

            switch (secim)
            {
                case 1:
                    // Yeni kitap ekleme işlemi
                    Console.WriteLine("Yeni kitap bilgilerini girin:");

                    Console.Write("Kitap Adı: ");
                    string kitapAdi = Console.ReadLine();

                    Console.Write("Yazar: ");
                    string yazar = Console.ReadLine();

                    Console.Write("Yayınevi: ");
                    string yayinevi = Console.ReadLine();

                    Console.Write("Sayfa Sayısı: ");
                    int sayfaSayisi;
                    if (!int.TryParse(Console.ReadLine(), out sayfaSayisi))
                    {
                        Console.WriteLine("Geçersiz sayfa sayısı!");
                        continue;
                    }

                    Console.Write("Yayın Tarihi(YYYY): ");
                    int yayinTarihi;
                    if (!int.TryParse(Console.ReadLine(), out yayinTarihi))
                    {
                        Console.WriteLine("Geçersiz yayın tarihi!");
                        continue;
                    }

                    Console.Write("Kitap ID: ");
                    int kitapKodu;
                    if (!int.TryParse(Console.ReadLine(), out kitapKodu))
                    {
                        Console.WriteLine("Geçersiz kitap ID!");
                        continue;
                    }

                    kutuphane.KitapKaydet(kitapAdi, yazar, yayinevi, sayfaSayisi, yayinTarihi, kitapKodu);
                    Console.WriteLine();
                    break;

                case 2:
                    // Kitap silme
                    Console.Write("Silinecek Kitap ID: ");
                    int silinecekKitapId;
                    if (!int.TryParse(Console.ReadLine(), out silinecekKitapId))
                    {
                        Console.WriteLine("Geçersiz kitap ID!");
                        continue;
                    }

                    // Kitap silme işlemi
                    kutuphane.KitapSil(silinecekKitapId);
                    Console.WriteLine();
                    break;

                case 3:
                    // Üye bilgilerini kullanıcıdan alma
                    Console.WriteLine("Yeni üye bilgilerini girin:");
                    Console.Write("Ad: ");
                    string ad = Console.ReadLine();

                    Console.Write("Soyad: ");
                    string soyad = Console.ReadLine();

                    Console.Write("Telefon: ");
                    string telefon = Console.ReadLine();
                    if (telefon.Length < 10)
                    {
                        Console.WriteLine("Geçersiz telefon numarası!");
                        continue;
                    }

                    Console.Write("Email: ");
                    string email = Console.ReadLine();

                    Console.Write("Üye ID: ");
                    int uyeId;
                    if (!int.TryParse(Console.ReadLine(), out uyeId))
                    {
                        Console.WriteLine("Geçersiz üye ID!");
                        continue;
                    }

                    kutuphane.UyeKaydet(ad, soyad, telefon, email, uyeId);
                    Console.WriteLine();
                    break;

                case 4:
                    //Üye silme
                    Console.Write("Silinecek Üye ID: ");
                    int silinecekUyeId;
                    if (!int.TryParse(Console.ReadLine(), out silinecekUyeId))
                    {
                        Console.WriteLine("Geçersiz üye ID!");
                        continue;
                    }

                    // Üye silme işlemi
                    kutuphane.UyeSil(silinecekUyeId);
                    Console.WriteLine();
                    break;

                case 5:
                    // Kitapları listeleme işlemi
                    kutuphane.KitaplariListele();
                    Console.WriteLine();
                    break;

                case 6:
                    // Üyeleri listeleme işlem
                    kutuphane.UyeleriListele();
                    Console.WriteLine();
                    break;

                case 7:
                    // Üyelerin kitap alması
                    Console.Write("Üye ID: ");
                    if (!int.TryParse(Console.ReadLine(), out uyeId))
                    {
                        Console.WriteLine("Geçersiz üye ID!");
                        continue;
                    }

                    Console.Write("Kitap ID: ");
                    int kitapId;
                    if (!int.TryParse(Console.ReadLine(), out kitapKodu))
                    {
                        Console.WriteLine("Geçersiz kitap ID!");
                        continue;
                    }

                    KitapUye kitapAl = new KitapUye
                    {
                        KitapKodu = kitapKodu,
                        UyeId = uyeId
                    };

                    kutuphane.KitapAl(uyeId, kitapKodu);
                    Console.WriteLine();
                    break;

                case 8:
                    // Hangi üye hangi kitabı almıştır?
                    Console.Write("Üye ID: ");
                    if (!int.TryParse(Console.ReadLine(), out int uyeIdForBooks))
                    {
                        Console.WriteLine("Geçersiz üye ID!");
                        continue;
                    }

                    kutuphane.UyeninAldigiKitaplariListele(uyeIdForBooks);
                    break;

                case 9:
                    // Kitapla üyeyi ayırmak (Kitap iade)
                    Console.Write("Üye ID: ");
                    if (!int.TryParse(Console.ReadLine(), out int uyeIdForReturn))
                    {
                        Console.WriteLine("Geçersiz üye ID!");
                        continue;
                    }

                    Console.Write("İade edilecek Kitap ID: ");
                    if (!int.TryParse(Console.ReadLine(), out int kitapIdForReturn))
                    {
                        Console.WriteLine("Geçersiz kitap ID!");
                        continue;
                    }

                    kutuphane.KitapIade(uyeIdForReturn, kitapIdForReturn);
                    break;

                case 10:
                    // Kitap yorumu ekleme
                    Console.Write("Kitap adını girin: ");
                    string kitapAdiForYorum = Console.ReadLine();

                    Console.Write("Yorumunuzu girin: ");
                    string yorum = Console.ReadLine();

                    kutuphane.KitapYorumuEkle(kitapAdiForYorum, yorum);
                    break;

                case 11:
                    // Kitap yorumu silme
                    Console.Write("Kitap adını girin: ");
                    string kitapAdiForYorumSil = Console.ReadLine();

                    kutuphane.KitapYorumuSil(kitapAdiForYorumSil);
                    break;

                case 12:
                    // Kitap yorumlarını listeleme
                    Console.Write("Kitap adını girin: ");
                    string kitapAdiForYorumListe = Console.ReadLine();

                    kutuphane.KitapYorumlariniListele(kitapAdiForYorumListe);
                    break;


                case 0:
                    Console.WriteLine("Çıkış yapılıyor...");
                    return;

                default:
                    Console.WriteLine("Geçersiz seçim!");
                    break;
            }
        }
        Console.WriteLine("Devam etmek için bir tuşa basın...");
        Console.ReadLine();
        Console.Clear();
    }
    private static string GetHiddenInput()
    {
        string input = "";
        ConsoleKeyInfo key;

        do
        {
            key = Console.ReadKey(true);

            if (key.Key == ConsoleKey.Backspace && input.Length > 0)
            {
                //Silme
                Console.Write("\b \b");
                input = input.Substring(0, input.Length - 1);
            }
            else if (key.Key != ConsoleKey.Enter)
            {
                Console.Write("*");
                input += key.KeyChar;
            }
        } while (key.Key != ConsoleKey.Enter);

        Console.WriteLine();
        return input;
    }
}
