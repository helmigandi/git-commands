Commands bagian 3
=================

### Branch
![git-branch](img/git-branch.png)
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

