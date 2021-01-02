# Git & Github

## Instalar
```bash
sudo apt update -y && sudo apt upgrade -y
sudo apt install -y git
```
## Configurar
```bash
git config --global user.name "Ezequiel Roldan"
git config --global user.email "ezeroldan@gmail.com"
git config --global color.ui auto
```

## Comandos

### Inicializar
- `git init [NAME]` Generar un Repositorio
- `git clone [URL]` Descargar un repositorio

### Informacion
- `git status` Listar nuevos o modificados archivos
- `git diff` Mostrar cambios en los archivos no en staged
- `git diff --cached` Mostrar los cambios para staged
- `git diff HEAD` Muestra todos los cambios
- `git diff --staged` Muestras las diferencias entre staging y la ultima version se archivos
- `git diff [BRANCH-A] [BRANCH-B]` Muestra diferencias entre dos branches
- `git blame [FILE]` Lista informacion de los cambios de un un archivo
- `git show [COMMIT]` Mostrar informacion sobre un commit
- `git show [FILE]` Mostrar informacion sobre un archivo
- `git log` Mostrar el historial de cambios

### Cambios
- `git add [./FILE]` Pasar los archivos a estado stages para commit
- `git commit -m "[MENSAJE]"` Commit todos los cambios
- `git commit --amend -m "[MENSAJE]"` Modificar el ultimo commit
- `git commit -am "[MENSAJE]"` Ejecutar add y commit
- `git reset [COMMIT]` Unstages los archivos, pero los preserva
- `git reset --soft` Revierte todo hasta el ultimo commit y conserva el codigo
- `git reset --hard` Revierte todo hasta el ultimo commit, pero los archivos untracked quedan intactos
- `git reset --hard [commit]` Descarta los cambios a un commit especifico
- `git clean -f -d` Los untracked son eliminados junto con los directorios
- `git rm [file]` Borra los archivos del working directory y stages los cambios
- `git stash` Muevo todo los archivos del working directory al stash

### Branching
- `git branch` Listar las branchs locales
- `git branch -a` Listar todas las branchs incluso las remotas
- `git branch [BRANCH]` Generar una nueva rama
- `git branch -m [BRANCH-A] [BRANCH-B]` Renonmbrar un branch
- `git checkout [BRANCH:master]` Cambiar a una branch
- `git checkout -b [BRANCH]` Ejecuta git branch y hace checkout
- `git merge [BRANCH]` Combina la branch con la actual
- `git branch -d [BRANCH]` Borra una branch

### Sincronizar
- `git pull` Descarga la historia y ejecuta los cambios
- `git push [ALIAS:origin] [BRANCH:master]` Sube todos los cambios a GitHub
- `git push -f [ALIAS:origin] [BRANCH:master]` Forzar actulizar los cambios
- `git push -u [ALIAS:origin] [BRANCH]` Sube un branch al repositorio remoto
- `git fetch [BOOKMARK]` Descarga toda la historia desde el repositorio
- `git remote add [NAME:origin] [URL]` Asociar con repositorio remoto
- `git remote remove [NAME:origin]` Eliminar la sincronizacion con el repositorio remoto

### Tagging
- `git tag -a [vx.x] -m [MENSAJE] [COMMIT]` Asociar la tag al ultimo commit
- `git push [ALIAS:origin] [TAG]` Subir la tag al github
- `git push [ALIAS:origin] --tag` Sube todas las tags

## GitHub
- **Issues:** Comentarios sobre el codigo, ya sea solicitar mejoras o indicar errores
- **Labels:** Categorias de Issues para organizar. Existen un conjunto por defecto.
- **Milestones:** Conjunto de issues que con fecha asginada, para ser agendados a resolver.
- **Assignee:** Lista de usuarios que se le asigna el Issue
- **Tags:** Se usan para marcar versiones del codigo,
- **Pages:** Para un usuario generar un repo con el nombre `[USER].github.io`. Para un repo generar la branch `git branch gh-pages`
