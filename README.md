
## CONFİGURATİONS

Switch> enable //Daha fazla işlem yapabilmek için “enable mode” a geçiş yapıyoruz.

Switch# conf t // Bu komutla konfig moda(Global Configuration Mode) geçiş yapıyoruz.

Switch(config)# hostname SW1 // Switch’e isim veriyoruz.

VLAN’LERIN YARATILMASI: //(VLAN bilgileri flash içerisinde “vlan.dat” dosyasında tutulur.

SW1# show vlan // VLan’ları görmek için kullanılır.

SW1(config)# vlan 2 // Vlan 2 oluşturuldu.

SW1(config-vlan)# name SUNUCULAR // Vlan 2’nin adı SUNUCULAR yapıldı.

SW1(config-vlan)# exit //Vlan 2’den çıkıldı.

SW1(config)# vlan 3 // Vlan 3 oluşturuldu.

SW1(config-vlan)# name BILGI_ISLEM // Vlan 3’ün adı BILGI_ISLEM yapıldı.

SW1(config-vlan)# exit //Vlan 3’ten çıkıldı.

SW1(config)# vlan 4 // Vlan 4 oluşturuldu.

SW1(config-vlan)# name MISAFIR // Vlan 4’ün adı MISAFIR yapıldı.

SW1(config-vlan)#end //Vlan 4’ten çıkıldı.

SW1# show vlan brief // komutu ile vlan’larımızın oluşup oluşmadığını kontrol edebiliriz.

## PORTLARA VLAN’LERIN ATANMASI:


SW1(config)# interface range fastEthernet 0/1-10 // interface config mode’da ilk 10 port aralığı seçildi

SW1(config-if-range)# switchport mode access // Port’ların son kullanıcı portu olduğu belirtildi.

SW1(config-if-range)# switchport access vlan 4 // 1 ile 10. port aralığındaki portlar Vlan 4 grubuna dahil edildi.

SW1(config-if-range)# exit // Çıkış yapıldı.

SW1(config)# interface range fastEthernet 0/11-20 // 11 ile 20. port aralığındaki portlar toplu olarak seçildi

SW1(config-if-range)# switchport mode access // Port son kullanıcı portu olarak atandı.

SW1(config-if-range)# switchport access vlan 2 // 11 ile 20. port aralığındaki portlar Vlan 2 grubuna dahil edildi.

SW1(config-if-range)# exit // Çıkış yapıldı.

SW1(config)# interface range fastEthernet 0/21-24 // 21 ile 24. port aralığındaki portlar toplu olarak seçildi

SW1(config-if-range)# switchport mode access // Port son kullanıcı portu olarak atandı.

SW1(config-if-range)# switchport access vlan 3 // 21 ile 24. port aralığındaki portlar Vlan 3 grubuna dahil edildi.

SW1(config-if-range)# exit // Çıkış yapıldı.

SW1(config)# do show vlan brief // komutu ile vlan’larımızın oluşup oluşmadığını kontrol edebiliriz.

SW1# show vlan brief // komutu ile vlan’larımızın oluşup oluşmadığını kontrol edebiliriz.

## TRUNK YAPILANDIRMASI:

SW1(config)# interface GigabitEthernet 0/1 // Gigabitethernet 0/1 interface’i seçildi.

SW1(config-if)# switchport mode trunk // TRUNK ile iki Switch’in VLAN’ları haberleştirilir.

SW1(config-if)# switchport trunk native vlan 1 // (def.değeri “vlan 1”) TRUNK’dan etiketsiz iletilecek VLAN numarası.

SW1(config-if)# switchport trunk allowed vlan all//(def.değeri “all”)TRUNK’dan geçmesine izin verilecek VLAN’ler

SWITCH YÖNETİM IP’Sİ YAPILANDIRMASI: (SVI - Switched Virtual Interface yapılandırması)

SW1(config)# interface vlan 3 // VLAN 3 seçildi

SW1(config-if)# ip address 192.168.3.11 255.255.255.0 // VLAN 3’ün ip adresi ve ağ geçidi verildi.

SW1(config-if)# no shutdown // VLAN 3 arayüzü erişime açıldı.

SW1(config-if)# exit // Çıkış yapıldı

SW1(config)# ip default-gateway 192.168.3.1 // Switch’e farklı ağdan erişebilmek için ağ geçidi atandı

SW1(config)# exit // Çıkış yapıldı

SW1# copy running-config startup-config // Değişikler kaydedildi.

## TELNET YAPILANDIRMASI:

SW1(config)# line vty 0 15 // 0 15 arası toplam 16 tane sanal telnet bağlantısı açtı.

SW1(config-line)# password cisco // password komutu ile telnet bağlantılarına şifre atandı.

SW1(config-line)# login // Login komutu ile telnet bağlantıları etkinleştirildi.

SW1(config-line)# exit // Çıkış yapıldı

SW1(config)# service password-encryption // Console, Telnet gibi parolalar basit bir algoritma ile şifrelendi.

SW1(config)# exit // Çıkış yapıldı

SW1# wr // Değişikler kaydedildi.

SW1(config)# enable secret cisco // enable moda’a geçerken şifre kullanımı sağlar.

Enable password den farkı burada yazılan şifre encyripted (md5 kriptolu) olarak gözükür.

SW1# wr // Değişikler kaydedildi.

SW1# show cdp neighbor // Komşu cihazlara hangi portta bağlanıldığını gösterir.

//diğer switchlere de aynı konfigürasyon yapılır.


