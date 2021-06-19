# Bash Scripting

## Script
```bash
#!/bin/bash
echo "Hola"
exit 0
```

- `chmod +x ./file.sh` Darle permisos de ejecucion
- `./file.sh` Ejecutarlo

## Variables

### Environment Variables
- `echo $VAR_NAME` Ver contenido de una variable del sistema
- `printenv` Listar las variables del sistema
- `printenv HOME` Listar contenido de una variable
- `export VAR="value"` Generar una variable del sistema
- `unset VAR` Remover una variable

#### Shell Variables
- `$PATH` Lista los directorios donde buscar los comandos executables
- `$HOME` Path absoluto del directorio del usuario actual
- `$USER` Nombre del usuario actual
- `$HOSTNAME` Nombre de la computadora
- `$HOSTTYPE` Tipo de computadora
- `$PS1` Prompt de la terminal
- `$PWD` Path del directorio actual
- `$OLDPWD` Imprimir directorio anterior
- `$IFS` Internal Field Separator (space,tab, newline)

### Parameter Expansion
- `${USER,}`  Lowercase primera letra (lcfirst)
- `${USER,,}` Lowercase todo (strtolower)
- `${USER^}`  Uppercase primera letra (ucfirst)
- `${USER^^}` Uppercase todo (strtoupper)
- `${#USER}`  Total de caracteres (strlen)
- `${USER:start:length}` Devuelve parte de un texto (substr)

## Command Substitution
- `result=$(command)` Obtener el resultado de un comando

## Arithmetic Expansion
- `$(( a + b))` Suma
- `$(( a - b))` Resta
- `$(( a * b))` Multiplicacion
- `$(( a / b))` Division
- `$(( (a + b) * c))` Orden de operaciones
- `$(( a ** b ))` Potencia 
- `$(( a % b ))` Obtener resto de una division
- `"scale=2; 5/2" | bc` Ejecutar operaciones con decimales

## Tilde Expansion
- `~` = `$HOME` Path del usuario actual
- `~root` Muestra path del usuario. EJ root
- `~-` = `$OLDPWD` Directorio anterior

## Brace Expansion
- `{a,b,c,d}` Remplaza la coma por un espacio
- `{1..9}` Geneara un lista del rango con un espacio
- `{a..z}` Lo mismo con letras
- `texto{1..2}` Genera texto1 texto2
- `texto{01..02}` Genera texto01 texto02

## Control Operators
- `;`  Ejecuta varios comandos, si uno falla el otro se ejecuta igual
- `|`  
- `||` Ejecuta varios comandos, si el primero falla el segundo se ejecutara
- `&`  Ejecutar comando en el background
- `&&` Ejecuta varios comandos, si el primero es OK el segundo se ejecutara
- `;;`
- `;&`
- `;;&`
- `|&`
- `()`
- `newline`

## Globbing
- `*` Cualquier cosa
- `?` Un caracter
- `[]` Cualquier caracter contenido
- `[0-9]` De 0 a 9
- `[a-z]` De a a Z

## Input Output and Redirection
- `0` Standard Input  stdin
- `1` Standard Output stdout
- `2` Standard Error  stderr

### Redirection Operatos
- `|` Pasa el resultado de un comando a otro
- `>` Redirecciona el output a un archivo (Truncate)
- `>>` Concatena el output a un archivo
- `<` Envia el contenido de un archivo a un comando
- `&` Redirecciona a otro file descriptor
- `&>` Suma el stdout y stderr
- `2>&1` Combinar el stderr con el stdout
- `2>file` Enviar errores (stderr) a un archivo
- `>/dev/null` Redirecciona el output a la nada

## Buscar comandos
- `type` Obtener info de un command
- `whereis` Mostrar ubicacion, source y manual
- `which command` Buscar ubicacion de un comando
- `man -k command` Buscar un comando segun keyword

## Requesting Input

### Positional Parameters
- `command $1 $2 $3` Valores ingresados por orden
- `${var:-default}` Usar valor defecto
- `$#` Count del total de parametros ingresados
- `$0` Indica el nombre del script
- `$@` Retorna todos los parametros ingresados (`"$@"`)
- `$*` Retorna todos los parmetros con IFS incluido
- `$?` Retorna el codigo de exit del command anterior

### Read command
- `read` Guarda lo ingresado en `$REPLY`
- `read var1 var2` Setea lo ingresado en `var1` y `var2`
- `read -p "Comentario" var` Promt, mostra una mensaje.
- `read -t 5` Timeout para esperar respuesta, en segundos.
- `read -s` Secret, no muestra al tipear, poner `echo` despues para dar enter
- `read -N 4` Limite de cantidad exacta de caracteres
- `read -n 4` Limite de cantidad maxima de caracteres

### Select command
```bash
PS3="Pregunta"
select var in options; do
  echo $var
  break
done
```
- Por defecto `RESPONSE` sera la variable con la respuesta
- `break` Rompe el loop de select
- `PS3` Tiene el mensaje de la pregunta

### getopts (--option -o)
- `getopts "a:b:" opt` Recupera las opcines
- `command -a value`
- `$OPTARG` Tendra el valor ingresadp

```bash
while getopts "a:b:" opt; do
  case "$opt" in
     a) ;;
     b) ;;
    \?) ;;
done
```

## Test command
- `test -options arguments` Evalue el exit status `$?`
- `[ value -option arguments ]` Se puede usar con []
- `exit 0` = true
- `exit 1` = false

### Internal Shell Conditions
- `[ -o opt ]` Option opt for set -o is on.
- `[ -R var ]` Variable var has been assigned a value and is a nameref.
- `[ -v var ]` Variable var has been assigned a value. var may name an array element.

### Integer Comparisons
- `[ n1 -eq n2 ]` n1 == n2 (Equal)
- `[ n1 -ne n2 ]` n1 != n2 (Not Equal)
- `[ n1 -gt n2 ]` n1 >  n2 (Greater)
- `[ n1 -ge n2 ]` n1 >= n2 (Greater or Equal)
- `[ n1 -lt n2 ]` n1 <  n2 (Less)
- `[ n1 -le n2 ]` n1 <= n2 (Less or Equal)

### String Conditions
- `[ s1 ]`         s1 is not null
- `[ -n s1 ]`      s1 has nonzero length
- `[ -z s1 ]`      s1 has zero length
- `[ s1 = s2 ]`    s1 identical s2
- `[ s1 == s2 ]`   s1 identical s2
- `[ s1 != s2 ]`   s1 not identical s2
- `[ s1 < s2 ]`    s1 precedes that of s2
- `[ s1 > s2 ]`    s1 follows that of s2
- `[[ s1 =~ s2 ]]` s1 matches regex s2

### File Conditions
- `[ -e f1 ]`     Exists
- `[ -a f1 ]`     Exists (Deprecated use -e)
- `[ -b f1 ]`     Exists and is a block special file
- `[ -c f1 ]`     Exists and is a character special file
- `[ -d f1 ]`     Exists and is a directory
- `[ -f f1 ]`     Exists and is a regular file
- `[ -g f1 ]`     Exists and its set-group-id bit is set
- `[ -G f1 ]`     Exists and its group is the effective group ID
- `[ -k f1 ]`     Exists and its sticky bit is set
- `[ -h f1 ]`     Exists and is a symbolic link. (Same as -L)
- `[ -L f1 ]`     Exists and is a symbolic link. (Same as -h)
- `[ -N f1 ]`     Exists and was modified after it was last read
- `[ -O f1 ]`     Exists and its owner is the effective user ID
- `[ -p f1 ]`     Exists and is a named pipe (FIFO)
- `[ -r f1 ]`     Exists and is readable
- `[ -s f1 ]`     Exists and has a size greater than zero
- `[ -S f1 ]`     Exists and is a socket
- `[ -u f1 ]`     Exists and its set-user-id bit is set
- `[ -w f1 ]`     Exists and is writable
- `[ -x f1 ]`     Exists and is executable
- `[ f1 -ef f2 ]` f1 and f2 are linked (same file)
- `[ f1 -nt f2 ]` f1 is newer than f2
- `[ f1 -ot f2 ]` f1 is older than f2

## Functions
- `functions` Lista las funciones
- `unfunction name` Elimina una funcion
- `autoload -U name` Cargar una funcion

```bash
name() {
  echo $1 # Positional Parameters
}

name "Param1"
```

## Compound commands

### if
- Valida el $? de un comando es 0
- `then` es el consecuant comand

```bash
if commad1 ; then # $? = 0
elif commad2 ; then # $? = 0
else # $? = 1
fi
```

### Array
- `numbers=(1 2 3 4)` Indexed array
- `${numbers[2]}` Muestra 3
- `${numbers[@]}` Obtener todos los elementos
- `${numbers[@]:1:2}` Imprime 2 3
- `numbers+=(5)` Agregar un item al array
- `unset numbers[2]` Eliminar item, no actuliza los key
- `${!numbers[@]}` Obtener los keys
- `${numbers[@]@Q}` Mostrar con catacteres ocultos
- `numbers[0]=1` Cambiar data por key
- `readarray -t nombre < file.txt` Genera array por cada linea
- `readarray -t nombre < <(ls ~)` Generar con process sustitution

### for
```bash
itmes=(1 2 3 4)
for item in "${itmes[@]}"; do
  echo $item
done
```

### Case
- Es recomendable poner la variable entre comillas
- Para evaluar cada caso se usa Globbing

```bash
variable=1
case "$variable" in
       [0-9]) echo "Caso 1";;
  [0-9][0-9]) echo "Caso 2";;
           *) echo "Caso default";;
esac
```

### While loop
- Repite el loop mientras la condicion retorne un exit 0 = true

```bash
mum=9
while [ $mum -gt 10 ]; do
  echo $mum
done
```

## Archivos & Directorios

### Navegar en archivos
- `ls` Listar archivos y carpetas
- `cd` Change directory - Navegar entre directorios
- `pwd` Imprimir directorio actual
- `mkdir` Crear un directorio
- `mkdir -p dir1/dir2/dir3` Generar directorios en cascada
- `rmdir` Remove directory (only works if empty)

#### Directorios
- `Home` ~ Donde esta cada usuario
- `bin` Binarios - Los comandos que se ejecutan en consola.
- `sbin` Sudo Binarios - Comandos que solo el sudo puede ejecutar
- `boot` Elementales para booter el sistema
- `cdrom` CD montados - Legacy
- `dev` Dispositovos
- `etc` Etcetera - Configuraciones globales del sistema
- `lib, lib32 lib64` Librerias - Para que las aplicaciones usen
- `media` mnt Donde se montan los dispositivos. media automatico y mnt manual
- `opt` Carpeta Opcional - Se instalan otras apps
- `proc` Procesos - Dond se almacenan la info de los procesos
- `root` Home folder del usuario root
- `run` Directorio temporario
- `snap` Directorio de apps snaps
- `srv` Server - Donde los achivos del server se guardan
- `sys` Sistema - Directorio temporario del sistema
- `tmp` Temporario - Donde se almacena session temporaria
- `usr` Donde las aplicaciones para el usuario se instalan
- `var` Variable - Archivos que varian de tamano

### Symbolic Links
- `ln -s ABS_PATH NAME` Generar el link simbolico

### Commands for Working with Files
- `touch` Creates a file or updates the timestamp on an existing file
- `cat` Outputs the full contents of a file
- `head` Returns the first X lines of a file starting at the top
- `tail` Returns the first X lines of a file starting at the bottom
- `cp` Copies a file or directory
- `rm` Removes a file or directory
- `mv` Moves a file or folder
- `less` Displays contents of file while allowing easy scrolling up and down
- `diff file1 file2` Comparar dos archivos
- `sdiff file1 file2` Comparar dos archivos con pantalla partida (side-by-side)
- `vimdiff file1 file2` Destacar diferencias en vim
- `cmp` Checks if two files are identical on a byte-by-byte level
- `colordiff` Compare the two files and observe the difference
- `sed 's/PATTERN/TEXT/'` Sustitucion de texto

### Finding Files and Directories
- `find DIRECTORIO -iname NOMBRE` Buscar por nombre
- `find DIRECTORIO -type(d f l) NOMBRE` Buscar por tipo de archivo y nombre
- `file ARCHIVO` Indica el tipo de un archivo
- `locate NAME` Buscar usan el index de archivos

### Searching in Files
- `grep -[i c n v r w e] PATTERNS [FILE]` Busca dentro de un archivo (global regular expression print)
  - `-i` Busqueda caseinsesitive
  - `-c` Total de macheos
  - `-n` Con lineas de numero
  - `-v` Buscar lo que no coincide
  - `-r` Recursivamente
  - `-w` Coincidir palabra entera
  - `-e` Expresion a buscar
  - `-o` Imprime solo el texto encontrado
- `strings ` Muestra los caracteres imprimibles de un archivo
- `cut -[d f] FILE` Remueve partes de cada linea de un archivo
  - `-d` Delimintador
  - `-f` Muestra Nth campo 
  - `cut -d' ' -f2,3 FILE` Obtener el segundo y tercer campo separando por espacio
- `sort -[b d f h n r] FILE` Ordena un archivo
- `tr '' ''` Translate un caracter
- `column -[t] FILE` Arma lista columnada
- `more` Paginador simple
- `less` Paginador mas complejo

### Permisos
- `groups USER` `id -Gn` Ver los grupos de un usuario
- `chmod [u g o a] [+- wrx] [file/folder]` Los permisos tambien son llamados modos
  - Entidad
    - *u* User
    - *g* Group
    - *o* Other
    - *a* All
  - Operacion
    - *+* Dar el Permiso
    - *-* Eliminar el Permiso
  - Permiso
    - *w* Write
    - *r* Read
    - *x* Execute

- `chgrp [OPTION] GROUP FILE` Cambia el grupo de un archivo
- `umask [-S] [mode]` 

### Compresion

#### .tar
- `tar cf ....tar` Generar archivo .tar
- `tar xf ....tar` Extraer archivo
- `tar tf ....tar` Mostrar contenido del archivo

#### .zip
- `gzip ...` Generar gzip de un archivo
- `gzip -d ....gz` Extraer archivo

## Switching Users and Running Commands as Others
- `su [username=root]` Loguearte como otro usuario manteniendo las variables del sistema
- `su - [username=root]` Loguearte a la cuenta del usuario 
- `sudo -i` Loguearte como usuario root
- `whoami` Muestra el usuario que estoy usando

## SSH
- `ssh user@host` Conectar al host
- `ssh -p port user@host` Se conecta mediante el puerto
- `ssh -D port user@host` Conecta y usa bind port

## Otros
- `sudo` Super Usuario DO
- `clear` Limpia la consola
- `history` Muestra el historial de comandos
- `echo $HISTSIZE` Muestra el max de comandos almacenados

## Monitorear Procesos
- `ps -[e f u p H]` Ver Procesos ejecutandose
  - `-e` Mostrar todos los procesos
  - `-f` Lista completa
  - `-u` Los procesos de un Usuario
  - `-p` Info de un proceso puntual
  - `-H` Muesta el arbol de procesos
- `ps aux` Muestra procesos activos detallados  
- `pstree` Muestra procesos en forma de arbol
- `top` Muestra los procesos  
- `htop` Muestra los procesos con mas info

### Foreground && Background Processes
- `command &` Inicia el comando en Background
- `CTRL` + `C` Mata el proceso
- `CTRL` + `Z` Suspende el proceso

- `bg [%num]` Enviar un procesos suspendido al Background
- `fg [%num]` Enviar un proceso 
- `kill [%num]`Matar un proceso
- `jobs [%num]` Listar los procesos

## Network
- `ping ...` Muestra ip de un dominio
- `who is ...` Detalles de un Dominio

- `dig ...` Retorna el DNS de un dominio
- `dig -x ...` Busqueda invertida de host

- `wget ...` Descargar un archivo
- `wget -c ...` Continua una descarga
- `wget -r ...` Descarga recursivamente archivos de una url

- `ifconfig` Muestra la info del red  
- `iwconfig` Muestra la info del wifi

### Transferring and Copying Files over the Network
- `sftp CLIENT` Conectarse a Servidor externo
- `lpwd` pwd en local
-`lls` ls en local
- `put FILE` Subir archivos al sevidor
- `quit` Salir del servidor remoto
- `scp FILE SERVER:/PATH` Copiar archivo al servidor remoto

## Informacion del Sistema
- `uname -a` Muestra info del sistema
- `date` Ver hora y fecha actual
- `cal` Muestra calendario del mes
- `uptime` Muestra uptime
- `df` Muestra espacio en disco
- `du` Muestra espacio usado
- `lsusb` Muestra las unidades USB
- `blkid` Muestra info de los discos
- `du -[s h] FILES` Uso del disco
  - `s` Muestra solo el size
  - `h` Human sizes

## Alias
- `alias` Listar todas los alias
- `alias name=''` Generar un Alias en el archivo de config
- `unlias name` Eliminar un Alias
- `echo "alias name='value'" >> ~/.zshrc` Agregar Alias al archivo de configuracion

## Scheduling Repeated Jobs with Cron

### Crontab
- `crontab FILE` Agrega un archivo a la tabla de cron jobs
- `crontab -l` Listar todos los cron jobs
- `crontab -e` Editar cron job
- `crontab -r` Eliminar todos los cron jobs

#### Formato de un cron job
`MIN HOR DIA MES SEM command`
- MIN = 0-59
- HOR = 0-23
- DIA = 1-31
- MES = 1-12
- SEM = 0-6 (0=SUN)

- `0,30`
- `*/2`
- `0-4`

#### Cron de Laravel:
`* * * * * php path/artisan schedule:run >> /dev/null 2>&1`


## Shellcheck
- [https://www.shellcheck.net/](https://www.shellcheck.net/)
- `sudo apt install shellcheck`
- `shellcheck file.sh`