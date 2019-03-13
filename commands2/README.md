Commands bagian 2
=================
### Staging area

![staging](https://github.com/helmiz/git-commands/blob/master/img/git-staging.png)

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

  * pilih s, untuk split, lalu tentukan baris atau potongan yang ingin dimasukan ke staging lalu dicommit.
  * Kita dapat melihat apa saja yang di stagging dengan cara
    ```
    git diff --staged
    ```

  * Untuk melihat apa saja yang tidak masuk staging
    ```
    git diff
    ```

### git reset hard
membatalkan perubahan di staging dan working(Bahaya!!!)
```
git reset --hard
```

### gitignore
tidak mengikutsertakan file yang tidak diinginkan(hasil compile)
```
gitignore
```

### remote repository (github)
- Membuat repository baru pada github
- Terdapat dua protokol https/ssh, bedanya protokol yang dipakai dan authentikasinya. Kalau ssh pakai username password dan public key(tidak usah masukin password) kalau https akan ditanya password.
- copy url yang ada di github dan daftarkan di repo lokal, _nama-alias dipakai untuk mengganti nama yang defaultnya origin_, lalu ketik:
  ```  
  git remote add nama-alias url-github
  ```
- untuk menegecek (push -> dupload, fetch -> download)
  ```
  git remote -v
  ```
- push repository lokal (-u untuk menset default remote yaitu github, hal ini dilakukan pada saat push pertama)
  ```
  git push -u git-belajar master
  ```

### clone
mendapatkan yang sudah ada diserver di download ke lokal
```
git clone nama_url
git clone nama_url nama_folder_beda
```
