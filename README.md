# Pandoc ile Markdown Dosyalarını Birleştirme ve Dönüştürme

Bu rehber, `pandoc` komut satırı aracını kullanarak birden fazla Markdown (`.md`) dosyasını nasıl birleştireceğinizi ve farklı formatlara (örneğin `.docx`) nasıl dönüştüreceğinizi açıklamaktadır.

## 1. Kurulum

Öncelikle `pandoc`'un sisteminizde kurulu olması gerekmektedir. Debian/Ubuntu tabanlı bir sistem kullanıyorsanız, aşağıdaki komut ile kolayca kurabilirsiniz:

```bash
sudo apt install pandoc
```

## 2. Temel Kullanım

`pandoc`, dosyaları komut satırında belirttiğiniz sıraya göre işler ve birleştirir. En basit kullanımı şu şekildedir:

```bash
pandoc giris.md gelisme.md sonuc.md -o cikti.docx
```

Bu komut:
- `giris.md`, `gelisme.md` ve `sonuc.md` dosyalarını sırasıyla okur.
- `-o cikti.docx`: Bu üç dosyayı birleştirerek `cikti.docx` adında tek bir Word belgesi oluşturur. `-o` parametresi, "output" yani çıktı dosyasını belirtmek için kullanılır.

## 3. Gelişmiş Seçenekler ve Örnek Kullanım

`pandoc`'un işlevselliğini artıran birçok parametre bulunmaktadır. İşte en sık kullanılanlardan bazıları:

- `--toc` (`--table-of-contents`): Belgenin başına otomatik olarak bir "İçindekiler" tablosu ekler. Bu tablo, belgenizdeki başlıklardan (H1, H2, H3 vb.) oluşturulur.
- `--file-scope`: Bu parametre, `pandoc`'un her bir dosyayı kendi bağlamında işlemesini sağlar. Özellikle başlık seviyelerinin, dipnotların ve referansların her dosyada doğru bir şekilde korunması için kritik öneme sahiptir. Dosyalar birleştirilirken veri bütünlüğünü ve başlık hiyerarşisini korur.

### Örnek Gelişmiş Komut

Aşağıdaki komut, birden fazla Markdown dosyasını birleştirirken hem "İçindekiler" tablosu ekler hem de her dosyanın bütünlüğünü korur:

```bash
pandoc trino_nessie_guide.md gitea_https_deployment_guide1.md keycloak_kubernetes_guide-1.md --file-scope --toc -o birlestirilmis_rehber.docx
```

Bu komutun açıklaması:
1. `trino_nessie_guide.md`, `gitea_https_deployment_guide1.md` ve `keycloak_kubernetes_guide-1.md` dosyaları belirtilen sırayla okunur.
2. `--file-scope` parametresi sayesinde her dosyanın başlık yapısı ve iç referansları korunur.
3. `--toc` parametresi ile birleştirilmiş belgenin en başına bir "İçindekiler" bölümü eklenir.
4. `-o birlestirilmis_rehber.docx` ile sonuç, `birlestirilmis_rehber.docx` adında bir dosyaya yazdırılır.