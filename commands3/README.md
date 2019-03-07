Commands bagian 3
=================

### Branch
- Head -> Ujung dari suatu branch, Head terbagi dua yaitu head dan HEAD.
  * HEAD yaitu Aktif yang berarti kita sedang berada di dalamnya
- Branch adalah Head yang dikasih nama contoh: 1.x
- Master (Branch Master) adalah Branch default yang otomatis dibikin pada saat bikin dan bisa diganti.
- Origin adalah pada saat clone, remote sumbernya dikasih nama default Origin.
- Untuk melihat branch yang ada di repository:
  ```
  git branch
  git branch -a
  ```
- Contoh kasus -> Membuat dua perubahan yang tidak saling berhubungan tetapi dua-duanya ingin dikerjakan secara bersamaan (bug fixing dan nambah fitur)
  * Membuat Branch
	```
	git branch nama_branch
	```
   * Cek Branch
     tanda bintang menunjukan tempat kita ada di branch mana (yang aktif).
	```
	git branch
	```
   * Pindah Branch
	```
	git checkout nama_branch_yang_dibuat
	```
   * Melihat daftar Branch
	```
	git log --oneline --all --decorate --graph
	```
