Git reflog çıktınıza göre, bazı önemli commitler mevcut ve bu commitlere geri dönebilirsiniz. Bu durumda, eski klasörlerinizi ve dosyalarınızı kurtarma şansınız yüksek. İşte yapmanız gereken adımlar:

### Adım 1: Reflog'dan Geri Dönmek İstediğiniz Commit'i Belirleyin
`git reflog` çıktısına göre, geri dönmek istediğiniz commit'i belirleyin. Örneğin, dosyalarınızı kurtarmak için geri dönmek istediğiniz commit `0315f17` hash değerine sahip olabilir.

### Adım 2: Geri Dönmek İçin Reset veya Checkout Kullanın
Eğer belirli bir commit'e geri dönmek istiyorsanız, `git reset` veya `git checkout` komutlarını kullanabilirsiniz.

#### Seçenek 1: Git Reset ile Geri Dönmek
Bu seçenek, çalışma dizininizi belirtilen commit'e geri getirir.

```sh
git reset --hard 0315f17
```
**Not:** `--hard` seçeneği, çalışma dizininizdeki tüm değişiklikleri kaybeder. Eğer mevcut durumdaki değişiklikleri kaybetmek istemiyorsanız, `--soft` veya `--mixed` seçeneklerini kullanabilirsiniz.

#### Seçenek 2: Git Checkout ile Yeni Bir Branş Oluşturmak
Belirli bir commit'e geçiş yapabilir ve bu commit'ten yeni bir branş oluşturabilirsiniz.

```sh
git checkout 0315f17
git checkout -b eski-durum
```

### Adım 3: Değişiklikleri Commit Edin
Eğer reset veya checkout sonrası istediğiniz duruma döndüyseniz, bu durumu yeni bir commit ile kaydedin.

```sh
git add .
git commit -m "Eski duruma geri döndüm"
```

### Adım 4: Yeniden Birleştirmek veya Devam Etmek
Eğer önceki durumunuza döndüyseniz ve yeni değişiklikler yapmaya devam etmek istiyorsanız, ana branşınıza geri dönüp değişikliklerinizi yeniden entegre edebilirsiniz.

```sh
git checkout main
git merge eski-durum
```

### Özet
1. `git reflog` kullanarak geri dönmek istediğiniz commit hash'ini belirleyin.
2. `git reset --hard <commit-hash>` veya `git checkout <commit-hash>` ile belirtilen commit'e geri dönün.
3. Değişiklikleri commit edin ve gerekirse ana branşınıza geri dönüp değişiklikleri birleştirin.

Bu adımları izleyerek eski klasörlerinizi ve dosyalarınızı kurtarabilirsiniz.



```
53e7156 (HEAD -> main, origin/main) HEAD@{0}: reset: moving to HEAD
53e7156 (HEAD -> main, origin/main) HEAD@{1}: checkout: moving from 0315f177cb36e290bc6ca5972393f0d0f31eac9e to main
0315f17 HEAD@{2}: commit (amend): Klasör isimlerini değiştirdim ve eksik klasörleri ekledim
dbc6a9a HEAD@{3}: commit: Klasör isimlerini değiştirdim ve eksik klasörleri ekledim
046742d HEAD@{4}: commit: Updated English Turkish Language
127c564 HEAD@{5}: commit: Updated Dark Mode And Styling
57a614b HEAD@{6}: commit: Updated Dark Mode
492b5ae HEAD@{7}: commit: Bars, Datas, Designs Updated
9bdd75c HEAD@{8}: commit: updated for sending mail
2d8a8ce HEAD@{9}: commit: Payment Process Updated
b62ecaf HEAD@{10}: commit: updated with barcode scanner
0efd85e HEAD@{11}: commit: Updated with data
53e7156 (HEAD -> main, origin/main) HEAD@{12}: checkout: moving from main to 53e71564be5b352e820b4091f4327329cde30e3a
53e7156 (HEAD -> main, origin/main) HEAD@{13}: commit: Updated Tabs algorithm and added cart function with Accordion List
d04e58e HEAD@{14}: commit: Added Biometric Log In and NFC read&write ; Basic design for Log In UI; Added Settings Screen UI
ee81023 HEAD@{15}: commit: Dashboard and Avatar Group for Online Users Updated
16d848b HEAD@{16}: commit: Updated Home Screen Components
3f5be13 HEAD@{17}: commit: Second Commit with HomeWindow Updating and Adding Button
c8c2952 HEAD@{18}: commit: First Commit With HomeWindow Changes
536cb20 HEAD@{19}: commit (initial): Initial commit
PS C:\Users\Baki\OneDrive\Desktop\React-Native\T32> 
```



