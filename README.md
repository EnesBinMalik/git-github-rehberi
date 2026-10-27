# 🚀 Git & GitHub Başlangıç Rehberi (Türkçe)

Sıfırdan başlayanlar için kısa, uygulamalı ve tamamen Türkçe Git/GitHub notları.
Kopyala-yapıştır komutlar, gerçek akış örnekleri ve sık yapılan hatalar.

> Bu rehber, öğrenme sürecinde tutulmuş notlardan derlenmiştir. İşine yararsa ⭐ vermeyi unutma!

---

## 📚 İçindekiler

1. [Git ve GitHub nedir?](#1-git-ve-github-nedir)
2. [Kurulum](#2-kurulum)
3. [İlk ayarlar](#3-ilk-ayarlar)
4. [Temel komutlar](#4-temel-komutlar)
5. [Dallar (branch)](#5-dallar-branch)
6. [Uzak depo (remote)](#6-uzak-depo-remote)
7. [Pull Request akışı](#7-pull-request-akışı)
8. [Geri alma: restore / revert / reset](#8-geri-alma-restore--revert--reset)
9. [.gitignore](#9-gitignore)
10. [Sık yapılan hatalar](#10-sık-yapılan-hatalar)
11. [Faydalı kaynaklar](#11-faydalı-kaynaklar)

---

## 1. Git ve GitHub nedir?

- **Git**: Bilgisayarında çalışan, dosyalarının geçmişini kaydeden sürüm kontrol sistemidir. İnternet gerektirmez.
- **GitHub**: Git depolarını internette barındıran platformdur. İş birliği, kod incelemesi ve portfolyo için kullanılır.

Kısaca: **Git = kayıt cihazı**, **GitHub = bulut + sosyal platform**.

---

## 2. Kurulum

**Windows:** https://git-scm.com/download/win adresinden indir, kurulumda varsayılan ayarları kabul et.

Kurulumu doğrula:

```bash
git --version
```

---

## 3. İlk ayarlar

Her commit'te görünecek kimlik bilgileri:

```bash
git config --global user.name "Adın Soyadın"
git config --global user.email "eposta@ornek.com"
git config --global init.defaultBranch main
```

Ayarları kontrol et:

```bash
git config --list
```

---

## 4. Temel komutlar

| Komut | Ne yapar? |
|---|---|
| `git init` | Bulunduğun klasörde yeni depo başlatır |
| `git status` | Değişen dosyaları gösterir |
| `git add .` | Tüm değişiklikleri sahneye alır |
| `git add dosya.txt` | Tek dosyayı sahneye alır |
| `git commit -m "mesaj"` | Değişiklikleri kaydeder |
| `git log --oneline` | Commit geçmişini kısa gösterir |
| `git diff` | Yapılan değişiklikleri gösterir |

### Tipik akış

```bash
mkdir projem && cd projem
git init
echo "# Projem" > README.md
git add README.md
git commit -m "İlk commit"
```

---

## 5. Dallar (branch)

Dal, ana koddan bağımsız çalışma alanıdır. Yeni özelliği ana kodu bozmadan geliştirmeni sağlar.

```bash
git branch                  # dalları listeler
git switch -c yeni-ozellik  # yeni dal oluşturup geçer
git switch main             # ana dala döner
git merge yeni-ozellik      # dalı ana dala birleştirir
git branch -d yeni-ozellik  # birleşmiş dalı siler
```

> İpucu: `git checkout` eski, `git switch` yeni ve daha okunaklı komuttur.

---

## 6. Uzak depo (remote)

GitHub'da boş bir repo oluştur, sonra:

```bash
git remote add origin https://github.com/KULLANICI/REPO.git
git branch -M main
git push -u origin main
```

Sonraki gönderimler için yalnızca:

```bash
git push
```

Başkasının değişikliklerini almak için:

```bash
git pull
```

---

## 7. Pull Request akışı

1. Yeni dal aç: `git switch -c ozellik`
2. Değişikliği yap ve commit'le.
3. Gönder: `git push -u origin ozellik`
4. GitHub'da **Compare & pull request** → açıklama yaz → **Create pull request**.
5. İnceleme sonrası **Merge pull request**.

İyi bir PR: küçük, tek konuya odaklı ve açıklaması net olur.

---

## 8. Geri alma: restore / revert / reset

| Durum | Komut | Etki |
|---|---|---|
| Dosyadaki değişikliği geri al | `git restore dosya.txt` | Commit'lenmemiş değişiklik silinir |
| Sahneden çıkar | `git restore --staged dosya.txt` | Dosya sahne dışına alınır |
| Commit'i güvenle geri al | `git revert <hash>` | Geçmişi bozmadan yeni "geri alma" commit'i ekler |
| Son commit'i sil | `git reset --soft HEAD~1` | Commit silinir, değişiklikler kalır |

> Ortak/uzak dallarda **revert**, yerel temizlikte **reset** tercih edilir.

---

## 9. .gitignore

Takip edilmemesi gereken dosyaları listeler:

```gitignore
node_modules/
.env
*.log
dist/
```

Başlangıç şablonları: https://github.com/github/gitignore

---

## 10. Sık yapılan hatalar

- ❌ `.env`, şifre veya API anahtarı commit'lemek → ✅ `.gitignore` kullan.
- ❌ Devasa `node_modules` klasörünü göndermek → ✅ ignore listesine ekle.
- ❌ Anlamsız commit mesajları (`update`, `fix`) → ✅ "Sepet toplamı hatası düzeltildi" gibi açıklayıcı yaz.
- ❌ `main` dalında doğrudan çalışmak → ✅ Her özellik için dal aç.
- ❌ `git push --force`'u ortak dalda kullanmak → ✅ Gerekiyorsa `--force-with-lease` kullan.

---

## 11. Faydalı kaynaklar

- Git resmi dokümantasyon: https://git-scm.com/doc
- GitHub Docs: https://docs.github.com
- GitHub Skills (ücretsiz, interaktif): https://skills.github.com
- Git ignore şablonları: https://github.com/github/gitignore
- Pro Git kitabı (ücretsiz): https://git-scm.com/book/tr

---

## 🤝 Katkı

Hata veya eksik görürsen issue açabilir ya da pull request gönderebilirsin.

## 📄 Lisans

MIT
