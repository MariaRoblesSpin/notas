# GIT: Comandos útiles de uso habitual 

## Iniciar un repositorio
Para iniciar una carpeta como un repositorio Git. Colocarse sobre la susodicha carpeta y ejecutar desde la terminal el siguiente comando: 
```
git init
```
## Configuración global
```
git config --global user.name "nombre"
git config --global user.email "email"
git config --global color.ui true
git config --global core.editor "nano" (Mac y Linux)
git config --global core.editor "notepad" (Windows)
```

## Comparaciones

### Working area vs. Staging area
```
git diff
```
### Staging area vs. repository
```
git diff --staged
```
### Working area vs. repository
```
git diff HEAD
```

## Guardar los cambios

### Para ver nuestro espacio de trabajo:
```
git status
```

### Añadir archivos, carpetas o extensiones a la staging area:
```
git add <nombre-del-archivo>
git add <nombre-de-la-carpeta>
git add *.<extensión-archivos>
git add * (añade todos los archivos de la carpeta)
```

### Añadir cambios al repositorio:
```
git commit
```
Salta el editor de texto para que añadas un mensaje extenso que explique el commit

```
git commit -m "mensaje en un línea para explicar el commit"
```

### Para ver el conjunto de los commits con el SHA1 en versión abreviada:
```
git log --oneline
```


## Deshacer

### Deshacer el último commit y dejar el área de trabajo como está.
```
git reset HEAD~1
```
~1 hace referencia a que retrocede un único commit. De ese número depende los pasos atrás en los commits.

### Deshacer el último commit y quitar también los cambios en el área de trabajo (se pierden los cambios).
```
git reset --hard HEAD~1
```
### Para desechar los cambios de un archivo y volver al estado del commit anterior:
```
git checkout -- <nombre-del-archivo>
```
### Para movernos a una etiqueta
```
git reset <nombre-del-tag>
```

## Tags (Para versiones)

### Crear tag:
```
git tag <nombre-del-tag>
```

### Borrar tag:
```
git tag -d <nombre-del-tag>
```

## Para recuperar lo deshecho
```
git reflog
```
Muestra un listado de todos los commits registrados y todo el movimiento entre ellos.

## Ramas

### Para crear una rama pero no moverte a ella
```
git branch <nombre-de-la-rama>
```
### Para crear una rama y moverte a ella
```
git checkout -b <nombre-de-la-rama>
```
### Para moverte a una rama, a un commit, a un tag
```
git checkout <nombre-de-la-rama>
git checkout <codigo-del-commit>
git checkout <nombre-del-tag>
```
### Renombrar ramas
```
git branch -m <nombre-de-la-rama-antigua> <nombre-de-la-rama-nueva>
```
### Borrar ramas
```
git branch -D <nombre-de-la-rama>
```
### Recuperar commit y rama
```
git reflog
git checkout <codigo-commit-elegido>
git checkout -b <nombre-rama>
```
## Merge (unir/absorber/mezclar ramas)

### Merge fastforward
Estando en rama01 sólo cambia el puntero a rama02. Los commits de ambas ramas tienen que conformar una única lista.
```
git merge <rama02>
```
### Merge no fastforward
```
git merge --no-ff <rama02>
```
Crea un nuevo commit que apunta a los dos últimos commit de las dos ramas mezcladas.
Cuando hay cambios en las dos ramas desde la separación el sistema exige un commit para hacer el merge.

## Crear comandos personalizados
```
git config alias.nombre-comando "secuencia de comandos sin el git entre comillas"
```
Por ejemplo uno para ver el graph de los logs:

```
git config alias.graph "log --graph --oneline --decorate --pretty"
```
