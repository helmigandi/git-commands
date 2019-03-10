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
- Contoh Kasus (Shared Repo Workflow):
![shared-repo-workflow](https://github.com/helmiz/git-commands/blob/master/img/shared-repo-workflow.png)

  1. Programmer A membuat project dengan tiga baris perubahan, setelah itu push pertama dengan `push -u gitlab master`.
  2. Programmer B clone sehingga mendapatkan hasil tiga perubahan dari si A.
  3. Programmer B menambahkan tiga baris pada project, Lalu commit dan push dengan `git push`. Masuklah perubahan baris pada Shared Repo Server menjadi enam.
  4. Programmer A juga mengadakan perubahan dua baris, commit dan push. Dalam hal ini akan di *Reject* karena di dalam Server Repo sudah ada perubahan si B maka si A harus pull dahulu
  5. Programmer A melakukan Pull. Jika tidak ada konflik maka Repo si A bertambah tiga baris dan akan melakukan commit (merge) automatis. Kalau ada konflik maka akan macet atau begitu di merge dia gagal jadi harus diedit dahulu untuk menyelesaikan konflik lalu commit manual.
  6. Programmer A push kembali maka Repo Server akan bertambah dua.
  7. Programmer B Fetch dan Merge untuk menambahkan baris dari Repo Server

### Pull / Merge Request


- Fork -> Mengcopy
