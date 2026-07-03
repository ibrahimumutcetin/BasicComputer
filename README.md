# Mimari Projesi

Bu proje, Proteus ortamında hazırlanmış bir devre simülasyonunu içermektedir. 

## Proje Hakkında
Simülasyon dosyası (`BasicComputer.pdsprj`) içerisinde bir I2C haberleşme altyapısı (SDA, SCL hatları) ve bu protokolün analizini sağlayan **I2C Protocol Debugger** (I2C Hata Ayıklayıcı) yer almaktadır. Ayrıca devrenin çeşitli noktalarındaki gerilim ve akım değerlerini gözlemlemek için **Voltmetre** ve **Ampermetre** cihazları ile zamanlama/frekans ölçümleri için **Counter/Timer** donanımları bulunmaktadır.

## Kullanılan Araçlar ve Bileşenler
- Proteus (ISIS) 
- I2C Protocol Debugger (SDA ve SCL hatları)
- DC Voltmetre ve Ampermetre
- Counter / Timer birimleri

## Nasıl Çalıştırılır?
1. Bilgisayarınızda **Proteus** yazılımının kurulu olduğundan emin olun.
2. Bu repoyu bilgisayarınıza klonlayın veya indirin.
3. `BasicComputer.pdsprj` dosyasına çift tıklayarak projeyi Proteus üzerinde açın.
4. Sol alt köşedeki **Play (Oynat)** butonuna basarak simülasyonu başlatın.
5. I2C iletişimini izlemek ve devrenin ölçümlerini görmek için simülasyon ekranındaki sanal test cihazlarının çıktılarını inceleyebilirsiniz.
