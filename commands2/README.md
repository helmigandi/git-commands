Commands bagian 2
=================
### Staging area
- Tempat persiapan dari working folder ke repository setelah di add dan sebelum di commit
- contoh kasus: saat mengerjakan suatu program untuk membuat fitur baru kemudian dapat info bahwa ada bug pada program yang kita kerjakan di program yang sama. lalu kita edit program tersebut untuk memperbaiki bug. dengan hal ini kita memiliki dua perubahan yaitu bug fix dan fitur baru yang belum jadi. sementara kita mau yang disimpan bug fix saja. jadi kita commit baris tertentu saja.
- Langkah-langkah:
  * untuk perubahan di stagging (hapus yang sudah di add agar tidak terpush)
    ```
    git reset
    ```
  
  * untuk add ke staging secara perbaris atau potongan
   ``` 
   git add -p
   ```
---pilih s, untuk split
---pilih baris yang ingin dimasukan ke staging lalu dicommit.
---git diff --staged
---melihat apa saja yang di stagging
---git diff
---melihat apa saja yang tidak masuk staging

-git reset --hard
--membatalkan perubahan di staging dan working(Bahaya!!!)

-gitignore
--tidak mengikutsertakan file yang tidak diinginkan(hasil compile)

-remote repository (github)
--buat repository baru pada github
--terdapat dua protokol https/ssh
--bedanya protokol yang dipakai dan authentikasinya.
--kalau ssh pakai username password dan public key(tidak usah masukin password) kalau https akan ditanya password.
--copy url yang ada di github dan daftarkan di repo lokal
-- lalu ketik:
--git remote add nama_alias url_github
--git remote -v
--untuk menegecek (push -> dupload, fetch -> download)
--git push -u git-belajar master
--push repository lokal (-u untuk menset default remote yaitu github, hal ini dilakukan pada saat push pertama)

-clone
--mendapatkan yang sudah ada diserver di download ke lokal
--git clone nama_url
--git clone nama_url nama_folder_beda
