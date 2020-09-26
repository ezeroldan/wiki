# Git & Github

## Instalar
```bash
sudo apt update -y && sudo apt upgrade -y
sudo apt install -y git
```

```bash
git config --global user.name "Ezequiel Roldan"
git config --global user.email "ezeroldan@gmail.com"
git config --global color.ui auto
```

## Comandos

### Inicializar

`git init [NAME]`  
Generar un Repositorio


`git clone [URL]`  
Descargar un repositorio

---

### Informacion

`git status`  
Listar nuevos o modificados archivos

`git diff`  
Mostrar cambios en los archivos no en staged

`git diff --cached`  
Mostrar los cambios para staged

`git diff HEAD`  
Muestra todos los cambios

`git diff --staged`  
Muestras las diferencias entre staging y la ultima version se archivos

`git diff [BRANCH-A] [BRANCH-B]`  
Muestra diferencias entre dos branches    

`git blame [FILE]`  
Lista informacion de los cambios de un un archivo

`git show [COMMIT]`  
Mostrar informacion sobre un commit

`git show [FILE]`  
Mostrar informacion sobre un archivo

`git log`  
Mostrar el historial de cambios

---

### Cambios

`git add [./FILE]`  
Pasar los archivos a estado stages para commit

`git commit -m "[MENSAJE]"`  
Commit todos los cambios

`git commit -am "[MENSAJE]"`  
Ejecutar add y commit

`git reset [COMMIT]`  
Unstages los archivos, pero los preserva

`git reset --hard`  
Revierte todo hasta el ultimo commit

`git reset --hard [commit]`  
Discards all history and changes back to the specified commit

`git rm [file]`  
Deletes the file from the working directory and stages the deletion  

---

### Branching

`git branch`  
Listar todas las branchs

`git branch [BRANCH]`  
Generar una nueva rama

`git checkout [BRANCH] master`  
Cambiar a una branch

`git merge [BRANCH]`  
Combina la branch con la actual

`git branch-d [BRANCH]`  
Borra una branch

---
### Sincronizar

`git pull`  
Descarga la historia y ejecuta los cambios

`git push [ALIAS] [BRANCH]`  
Sube todos los cambios a GitHub  

`git fetch [BOOKMARK]`  
Descarga toda la historia desde el repositorio
