Commands bagian 3
=================

### Branch
![git-branch](https://github.com/helmiz/git-commands/blob/master/img/git-branch.png)
- Head -> Ujung dari suatu branch, Head terbagi dua yaitu head dan HEAD.
  * HEAD yaitu Aktif yang berarti kita sedang berada di dalamnya
- Branch adalah Head yang dikasih nama contoh: 1.x
- Master (Branch Master) adalah Branch default yang otomatis dibikin pada saat bikin dan bisa diganti.
- Origin adalah pada saat clone, remote sumbernya dikasih nama default Origin.
- Untuk melihat branch yang ada di repository:
  ```
  git branch
  git branch -a (untuk cek origin)
  ```

#### Membuat dua Branch
Contoh kasus -> Membuat dua perubahan yang tidak saling berhubungan tetapi dua-duanya ingin dikerjakan secara bersamaan (bug fixing dan nambah fitur)
- Membuat Branch
	```
	git branch nama_branch
	```
- Cek Branch
     tanda bintang menunjukan tempat kita ada di branch mana (yang aktif).
	```
	git branch
	```
- Pindah Branch
	```
	git checkout nama_branch_yang_dibuat
	```
- Melihat daftar Branch
	```
	git log --oneline --all --decorate --graph
	```
- Push Branch
	```
	git push origin nama_branch
	```

#### Menggabungkan dua branch
Setelah membuat branch disini kita akan mencoba menggabungkan dua buah branch dengan cara:
- Pindah ke Branch Master
	```
	git checkout master
	```
- Mengambil perubahan pada branch ke master
	```
	git merge nama_branch_yang_mau_ditarik
	```
- Kalau edit dibaris yang berbeda maka langsung digabungkan tetapi jika edit dibaris yang sama maka akan timbul _**conflict**_. hal tersebut akan dinyatakan dengan dua bagian yaitu marker awal `<<<<<< HEAD` dan marker akhir `======` yang berada di master, sedangkan bagian branch ditandai dengan marker `>>>>>>>> nama_branch`.
- Cara reconsile harus ngobrol, versi mana yang dipakai dengan orang terakhir commit.
- Untuk perbaikan _**conflict**_ tinggal di edit seperti biasa versi mana yang ingin dipakai dan yang tidak dipakai dapat dihapus dengan markernya. Setelah itu tinggal di commit.
- Hapus branch yang tidak terpakai di lokal
	```
	git branch -d nama_branch
	```
- Hapus branch yang tidak terpakai di remote
bisa masuk ke github lalu delete branch atau dengan cara:
	```
	git push origin :nama_branch
	```
### Pull & Fetch
- Perintah git pull akan mengambil commit terbaru lalu otomatis menggabungkan (merge) dengan branch yang aktif.
- Sedangkan git fetch akan mengambil commit saja. Perintah git fetch tidak akan langsung melakukan merge.
	```
	git pull origin master
	git fetch origin master
	```
- Pada kode di atas Artinya kita akan mengambil commit dari branch master pada repository remote. origin adalah nama remote-nya.
- Pemakaian Pull & Fetch
  * Apabila kita sudah melakukan commit di repository lokal, maka yang kita gunakan adalah git fetch Karena untuk mencegah terjadinya bentrok.
  * Perintah git fetch akan mengambil commit terbaru dan menyimpannya di branch origin/master.
  * Sedangkan apabila kita tidak pernah melakukan apa-apa di lokal repository, kita bisa menggunakan git pull.
  * Perintah git pull akan mengambil commit terbaru ke branch origin/master dan langsung menggabungkannya dengan branch master (lokal).

### Shared Repository Workflow
![shared-repo-workflow](https://github.com/helmiz/git-commands/blob/master/img/shared-repo-workflow.png)

  1. Programmer A membuat project dengan tiga baris perubahan, setelah itu push pertama dengan `push -u gitlab master`.
  2. Programmer B clone sehingga mendapatkan hasil tiga perubahan dari si A.
  3. Programmer B menambahkan tiga baris pada project, Lalu commit dan push dengan `git push`. Masuklah perubahan baris pada Shared Repo Server menjadi enam.
  4. Programmer A juga mengadakan perubahan dua baris, commit dan push. Dalam hal ini akan di *Reject* karena di dalam Server Repo sudah ada perubahan si B maka si A harus pull dahulu
  5. Programmer A melakukan Pull. Jika tidak ada konflik maka Repo si A bertambah tiga baris dan akan melakukan commit (merge) automatis. Kalau ada konflik maka akan macet atau begitu di merge dia gagal jadi harus diedit dahulu untuk menyelesaikan konflik lalu commit manual.
  6. Programmer A push kembali maka Repo Server akan bertambah dua.
  7. Programmer B Fetch dan Merge untuk menambahkan baris dari Repo Server

### Feuture Branch Workflow
- Feature Branch adalah Branch terpisah untuk membuat feature sehingga setelah selesai dapat di merge. Hal ini membuat pekerjaan yang baru tidak bercampur dengan yang lain.
- Kalau tidak memakai feuture branch maka commitnya akan bercampur dengan yang lain dan tidak terurut pada saat dimerge. Dengan kata lain menghindari commit dimaster.
- Hal ini bermanfaat pada saat undo. Pada saat feature yang kita kerjakan tidak jadi dipakai, kita hanya undo pada saat merge feature tersebut saja.

![feature-branch-workflow](https://github.com/helmiz/git-commands/blob/master/img/feature-branch-workflow.png)

1. Kita mempunyai:
   * Shared Repo pada sebelah kanan gambar.
   * Programmer A, B dan Lain.
   * Masing-masing mempunyai Mirror Shared Repo (MR) kotak kuning dan Master Lokal (ML).
   * Masing-masing programmer sudah ada tiga commit (garis hitam).
2. Programmer A membuat Branch untuk membuat feature-x dengan `git branch fitur-x` dan pindah ke branch tersebut dengan `git checkout fitur-x` (gambar kotak dengan garis abu-abu).
3. Programmer A membuat tiga commit (garis tiga pada kotak Fx dengan garis abu-abu).
4. Programmer Lain menambahkan empat commit (garis empat pada kotak Shared Repo dengan garis kuning).
5. Programmer A ingin melihat apa yang Programmer Lain kerjakan maka si A bisa langsung pull dengan cara pindah dulu ke master `git checkout master` dan kemudian pull `git pull` (garis tengah warna merah).
6. Commit Programmer Lain akan masuk ke dalam MR dan ML punya si A tanpa konflik dan tidak akan mempengaruhi pekerjaan si A di Fx (garis empat pada kotak MR dan ML si A dengan warna kuning).
7. Programmer A akan merge Fx dengan yang ada di Master Lokal (ML) caranya pindah dulu `checkout master` dan merge `git merge fitur-x` (garis warna abu-abu pada kotak ML).
8. Setelah di merge ke master, Programmer A push ke Shared Repo (garis abu-abu pada kotak Shared Repo).
9. Feature X dapat dipush dan tidak. Dipush kalau feature tersebut dikerjakan bersama atau Sharing dengan Programmer Lain (garis abu-abu pada kotak shared repo).

### Pull / Merge Request
- Seorang Programmer tidak mau memberikan hak menulis (wirte) kepada orang lain, akan tetapi orang lain boleh baca dan copy. Tetapi jika ada yang ingin menambahkan maka Seorang Programmer tersebutlah yang ambil atau pull. Jadi Programmer tersebutlah yang mengontrol. Lalu Programmer lain dapat menambahkan hak menulis dengan _pull / merge request_.
- Fork -> Mengcopy

![pull-merge-request](https://github.com/helmiz/git-commands/blob/master/img/fpull-merge-request.png)

1. Programmer A mempunyai Project dengan beberapa commit di Local A, Lalu si A push ke Remote punya si A sendiri.
2. Programmer B ingin ikut Project yang dikerjakan si A dan menambahkan atau memodifikasi beberapa bagian Project tersebut. Dengan begitu maka si B akan melakukan _Fork_ ke Remote B.
3. Programmer B melakukan Clone.
4. Programmer B melakukan coding dan perubahan. Lalu si B push ke Remotenya ia Sendiri menjadi delapan commit.
5. Programmer B ingin apa yang ia tambahkan dapat dipakai oleh orang banyak. Dikarenakan Project tersebutnya punya si A dan yang mempopulerkan si A maka si B membuat _pull request_.
6. Programmer A akan pull dari Remote B. Lalu si A akan bikin Branch Review si B.
7. Jika Bagus maka si A akan Merge punya si B.
8. Programmer A lalu push ke Remote A.
