# MerOS - Basit İşletim Sistemi

**MerOS**, Rust dilinde yazılmış, basit bir işletim sisteminin temel özelliklerine sahip bir projedir. Bu proje, sistem programlaması ve işletim sistemi çekirdeği geliştirme konularında bir başlangıç sağlamayı amaçlar. Şu anda, temel olarak ekranda "MerOS" yazısını gösterebilen bir yapı sunmaktadır.

## İçerik

- **No-Std Çekirdek**: Rust’ın `std` kütüphanesi olmadan, temel `core` kütüphanesiyle çalışan bir çekirdek.
- **VGA Ekran Çıkışı**: Ekrana basit bir "MerOS" yazısı yazdırmak için VGA tamponu kullanılır.
- **Bootloader Desteği**: ISO dosyası oluşturulup QEMU üzerinden çalıştırılabilir.

## Gereksinimler

- Rust kurulu olmalıdır. [Rust Kurulum Kılavuzu](https://www.rust-lang.org/tools/install)
- `qemu` kurulu olmalıdır. QEMU, işletim sisteminizi sanal ortamda çalıştırmanıza olanak sağlar. [QEMU Kurulum Kılavuzu](https://www.qemu.org/download/)
- `bootimage` aracı ile bootable ISO imajları oluşturmak için gerekli araçlar.

## Kurulum

1. **Proje Bağımlılıklarını Yükleme**:
   ```bash
   cargo install bootimage
   ```

2. **Hedef Platformu Ekleme**:
   `x86_64-unknown-none` hedefini ekleyin:
   ```bash
   rustup target add x86_64-unknown-none
   ```

3. **Proje Bağımlılıklarını Güncelleme**:
   `Cargo.toml` dosyasına aşağıdaki bağımlılığı ekleyin:
   ```toml
   [dependencies]
   bootimage = "0.10"
   ```

## Çalıştırma

1. **ISO İmajı Oluşturma**:
   Çekirdeğinizi derleyin ve bir ISO dosyası oluşturun:
   ```bash
   cargo build --target x86_64-unknown-none
   cargo bootimage --target x86_64-unknown-none
   ```

2. **QEMU ile Çalıştırma**:
   ISO dosyasını QEMU ile çalıştırmak için aşağıdaki komutu kullanın:
   ```bash
   qemu-system-x86_64 -cdrom target/x86_64-unknown-none/debug/meros.iso
   ```

## Özellikler

- **VGA Ekran Çıkışı**: Sistem açıldığında "MerOS" yazısını ekranda görüntüler.
- **Basit Çekirdek Yapısı**: Gömülü sistemler ve işletim sistemleri geliştirmek için temel yapı taşları sağlar.
- **No-Std Kullanımı**: Gömülü ve düşük seviyeli sistemler için `std` kütüphanesi yerine `core` kütüphanesi kullanılır.

## Katkı

Bu projeye katkı sağlamak için aşağıdaki adımları izleyebilirsiniz:

1. Projeyi kendi bilgisayarınıza klonlayın:
   ```bash
   git clone https://github.com/hacimertgokhan/meros.git
   ```
2. Değişiklik yapın ve pull request gönderin.

---

**Not**: Bu proje, işletim sistemi çekirdeği geliştirme sürecine yeni başlayanlar için bir örnektir. Geliştirmeye devam edebilir ve yeni özellikler ekleyebilirsiniz.