## 1. Configuración Inicial

### Creación del Repositorio local
```bash
# para iniciar git en el directoria que estemos
git init
# para crear el taller git_taller y la carpeta de configuracion de .git
git init git_taller
```
# Este comando inicializa un nuevo repositorio Git en un directorio llamado 'git_taller'.
# Si el directorio no existe, se creará pero primero inicia git.

### Configuración de Git con tu usuario y correo 
Configura tu nombre y correo electrónico:
```bash
# configurar nombre de usuario
git config --global user.name "Albert-MoDz"
# configurar correo electrónico
git config --global user.email "escobar.alberto@correounivalle.edu.co"
```
# Estos comandos configuran tu identidad de Git de forma global.
# Reemplaza "Nombre Estudiante" con tu nombre real y "email@estudiante.com" con tu correo de GitHub.
# Esta información se adjuntará a tus commits.

## 2. Creación de Ramas y Commits en el proyecto

Crea una nueva rama y realiza los commits iniciales:

```bash
git checkout -b feature
# Esto crea una nueva rama llamada 'feature' y cambia a ella.

echo "Texto inicial" > archivo.txt
# Esto crea un nuevo archivo llamado 'archivo.txt' con el contenido "Texto inicial".

git add archivo.txt
# Esto prepara el nuevo archivo para el commit.

git commit -m "Commit inicial"
# Esto crea el primer commit con los cambios preparados.

echo "Texto agregado en feature" >> archivo.txt
# Esto añade nuevo texto al 'archivo.txt'.

git commit -am "Segundo commit en feature"
# Esto prepara todos los archivos modificados y crea un segundo commit en un solo paso.
```

Realiza al menos un commit más en la rama `feature`.
# Debes hacer al menos un commit más en la rama 'feature' para practicar el trabajo con múltiples commits.

## 3. Fusión y Rebase

### Técnica de Fusión
```bash
git checkout master
# Esto cambia de vuelta a la rama master.

git merge feature
# Esto fusiona la rama 'feature' en 'master', creando un nuevo commit de fusión.
```

### Técnica de Rebase
Después de revertir la fusión:
```bash
git reset --hard HEAD~1
# Esto deshace la fusión anterior moviendo el puntero HEAD y de la rama un commit hacia atrás.

git rebase feature
# Esto replica los commits de 'feature' sobre 'master', creando un historial lineal.
```

## 4. Cherry-pick y Reflog

### Cherry-pick
Crea un hotfix y aplícalo a master:
```bash
git checkout -b hotfix
# Esto crea y cambia a una nueva rama 'hotfix'.

echo "Corrección urgente" >> archivo.txt
# Esto añade una línea a 'archivo.txt' para simular una corrección crítica.

git commit -am "Hotfix"
# Esto hace commit de los cambios en la rama 'hotfix'.

git checkout master
# Esto cambia de vuelta a la rama master.

git cherry-pick hotfix
# Esto aplica el commit de la rama 'hotfix' a 'master'.
```

### Reflog
Explora el historial del repositorio y restaura un commit perdido usando `git reflog`.
# El reflog muestra un registro de dónde han estado tus referencias HEAD y de rama.
# Puedes usarlo para encontrar y restaurar commits que ya no son visibles en el log normal.

## 5. Gestión de Conflictos

Crea y resuelve conflictos intencionalmente:

```bash
git checkout feature
# Cambia a la rama 'feature'.

echo "Cambio en feature" > conflicto.txt
# Crea un nuevo archivo con contenido que entrará en conflicto.

git commit -am "Cambio en feature"
# Hace commit del cambio en la rama 'feature'.

git checkout master
# Cambia de vuelta a la rama 'master'.

echo "Cambio en master" > conflicto.txt
# Crea el mismo archivo con contenido diferente en 'master'.

git commit -am "Cambio en master"
# Hace commit del cambio en la rama 'master'.

git merge feature
# Intenta fusionar 'feature' en 'master'. Esto causará un conflicto.
```
