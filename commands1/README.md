Commands Bagian 1
===========
### config
untuk memulai git menambahkan nama dan email
```markdown
git config --global user.email "sugandihelmi@gmail.com"
git config --global user.name "Helmi"
```

### git init
untuk membuat repository baru di local
contoh: 
```markdown
git init belajar-git
```

### git status
untuk melihat status sudah di track / monitor atau belum oleh git
```markdown
git status
```

### git add
untuk mentrack / monitor ke git
contoh: 
1. untuk semua file:
   ```markdown
   git add .
   ```
2. untuk per file
   ```markdown
   git add nama_file
   ```

### git commit
untuk menyimpan file
contoh:
```markdown
git commit -m "pesan / keterangan commit"
```

### git diff
untuk melihat perbedaan
```markdown
git diff
```

### git log
melihat perubahan history
contoh:
```markdown
git log --oneline
```

### git diff log
melihat perbedaan antar versi
contoh:
```markdown
git dif commitId_sebelum..commitId_sesudah
```
