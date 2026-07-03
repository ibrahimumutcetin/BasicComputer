*For English, please see [README_EN.md](README_EN.md)*

# Basic Computer (Basit Bilgisayar) Simülasyonu

Bu proje, Proteus ortamında **temel mantık kapıları ve entegre devreler (IC)** kullanılarak tasarlanmış bir Basit Bilgisayar (Basic Computer) simülasyonunu içermektedir. Temel bilgisayar mimarisini ve işlemcilerin çalışma mantığını anlamak için harika bir örnektir.

## Projede Kullanılan Temel Bileşenler (Entegreler)

Proje, gerçek hayatta da kullanılan standart 74LS serisi mantık entegreleri ve bellek birimleriyle oluşturulmuştur:

- **74LS181 (ALU - Aritmetik Mantık Birimi):** Bilgisayarın kalbidir. Toplama, çıkarma, mantıksal AND/OR gibi matematiksel ve mantıksal işlemleri gerçekleştirir.
- **74LS173 (4-bit D-Tipi Yazmaçlar / Registers):** Verileri geçici olarak saklamak için kullanılır. Genellikle Akümülatör (A Register), B Register, Instruction Register (Buyruk Yazmacı) veya Output (Çıkış) yazmacı olarak görev yaparlar.
- **74LS161 (Senkron 4-bit Sayıcı / Counter):** Program Sayacı (Program Counter - PC) olarak kullanılır, bellekteki (RAM/ROM) hangi komutun çalıştırılacağını takip eder.
- **74LS138 (3-to-8 Dekoder):** Adres çözme veya komutların (instruction) kodunu çözüp ilgili kontrol sinyallerini (Control Word) üretmek için kullanılır.
- **74LS245 (Sekizli Veri Yolu Alıcı-Verici / Bus Transceiver):** Birimlerin ortak Veri Yolu (Data Bus) ile iletişim kurmasını sağlar, verinin yönünü kontrol eder.
- **RAM (Rastgele Erişimli Bellek):** Program komutlarının ve verilerin depolandığı ana bellek birimidir.
- **Logic State & Logic Probe:** Devreye dışarıdan manuel olarak "1" veya "0" sinyalleri vermek (örneğin veri girmek veya kontrol sinyallerini test etmek) ve yollardaki sinyalleri gözlemlemek için kullanılır.

## Toplama ve Çıkarma İşlemi Nasıl Yapılır?

Simülasyon üzerinde toplama ve çıkarma gibi işlemler temelde **74LS181 ALU (Aritmetik Mantık Birimi)** tarafından yapılır. Eğer işlemci tam otomatik (Control Unit ile) çalışıyorsa RAM'e küçük bir program yazılır. Eğer manuel moddaysa (Logic State anahtarlarıyla kontrol ediliyorsa), şu adımlar izlenir:

### 1. Toplama İşlemi (A + B)
1. **Veri Yükleme:** Toplanacak birinci sayıyı Veri Yoluna (Data Bus) verin ve **Akümülatör (A Register)**'a kaydedin (Load sinyalini aktif ederek).
2. **İkinci Veriyi Yükleme:** Toplanacak ikinci sayıyı Veri Yoluna verin ve **B Register**'a kaydedin.
3. **ALU Ayarı:** 74LS181 entegresinin kontrol pinlerini (S0, S1, S2, S3 ve M) **Toplama (ADD)** moduna getirin. 
   - *Not: 74LS181 için genellikle `M=0` (Aritmetik işlem) ve Seçim (S) pinleri `S3 S2 S1 S0 = 1001` (A+B) olarak ayarlandığında toplama yapılır.*
4. **Sonucu Görme:** ALU'nun çıkışları iki sayının toplamını verecektir. Bu sonucu dilerseniz tekrar bir yazmaca veya doğrudan çıkış ekranına yönlendirebilirsiniz.

### 2. Çıkarma İşlemi (A - B)
1. **Veri Yükleme:** Çıkarılacak (eksilen) birinci sayıyı **Akümülatör (A Register)**'a kaydedin.
2. **İkinci Veriyi Yükleme:** Çıkan sayıyı **B Register**'a kaydedin.
3. **ALU Ayarı:** 74LS181 entegresinin kontrol pinlerini **Çıkarma (SUBTRACT)** moduna getirin.
   - *Not: 74LS181 için çıkarma işlemi (A-B) genellikle `M=0` ve Seçim pinleri `S3 S2 S1 S0 = 0110` olarak ayarlanarak gerçekleştirilir.*
4. **Sonucu Görme:** ALU çıkışında oluşan sonuç (A-B) değeridir. Bu değer veri yolu (bus) üzerinden ilgili birime aktarılabilir.

## Nasıl Çalıştırılır?
1. Bilgisayarınızda **Proteus** yazılımının kurulu olduğundan emin olun.
2. Bu repoyu bilgisayarınıza klonlayın veya indirin.
3. `BasicComputer.pdsprj` dosyasına çift tıklayarak projeyi Proteus üzerinde açın.
4. Sol alt köşedeki **Play (Oynat)** butonuna basarak simülasyonu başlatın.
5. `Logic State` butonlarına (kırmızı/mavi kareler) tıklayarak sinyalleri 1 veya 0 yapabilir, devrenin tepkisini `Logic Probe` veya LED'ler üzerinden gözlemleyebilirsiniz.
