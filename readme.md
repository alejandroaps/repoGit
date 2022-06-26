11) Deshacer el último commit (perdiendo los cambios realizados en el working copy)
- ¿Qué comando utilizaste en el paso 11? ¿Por qué?
git reset --hard HEAD~1 
Con el comando reset se restaura a un estado indicado el repositorio git, indicándole la posición anterior de HEAD con HEAD~1 para volver al estado anterior al del commit que hay que deshacer.
Es hard porque perdemos los cambios en el working copy que es la carpeta del proyecto



12) Rehacer el último commit (el que acabamos de deshacer)
¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?
En primer lugar: git reflog
Con esto puedo ver todo los movimientos de HEAD:
e6cf029 (HEAD -> styled, origin/main, main) HEAD@{0}: reset: moving to HEAD~1
6081f31 HEAD@{1}: commit: modify git-nuestro.md in styled
e6cf029 (HEAD -> styled, origin/main, main) HEAD@{2}: checkout: moving from main to styled
e6cf029 (HEAD -> styled, origin/main, main) HEAD@{3}: commit (initial): add file git-nuestro.md

y ahora: git reset --hard 6081f31
Para volver a tener el estado '6081f31' que es el del comnit que quiero restaurar y es hard porque quiero esos cambios en mi working copy



13) Hacer un merge con ‘master’ (styled absorbe a master)
El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?
No pero no se produce el merge:
$ git merge master
merge: master - not something we can merge
No hay nada que mergear ya la rama styled esta creada a partir del primer commit en main y la rama main no tiene commits en paralelo con la rama styled




19) Hacer un merge de “htmlify” en “styled” (styled absorbe a htmlify)
El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?
Si porque en ambas ramas hay commits que afectan al fichero git-nuestro.md





21) Desde “master”, hacer un merge con “styled”
El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?
No, porque la rama styled contiene el único commit de la rama main






25) Dibujar el diagrama
¿Qué comando o comandos utilizaste en el paso 25?
git log --graph








26) Hacer un merge “no fast-forward” de “title” en “master” (master absorbe a title)
El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?
Si porque la rama title esta basada en la rama main y en la rama main no hay commits en paralelo a la rama title por lo que se añade solo el commit que esta en la rama title en la rama main






27) Deshacer el merge (sin perder los cambios del working copy)
¿Qué comando o comandos utilizaste en el paso 27?
git reset HEAD~1
No es hard porque no querremos perder los cambios en el working copy









28) Descartar los cambios
¿Qué comando o comandos utilizaste en el paso 28?
git restore git-nuestro.md







29) Eliminar la rama “title”
¿Qué comando o comandos utilizaste en el paso 29?
git branch -D title










30) Rehacer el merge que hemos deshecho
¿Qué comando o comandos utilizaste en el paso 30?
Primero: git reflog
Con el que veo la siguiente informacion:
380f8db (HEAD -> main, origin/styled, styled) HEAD@{0}: reset: moving to HEAD~1
1ae1cab (origin/main) HEAD@{1}: merge title: Merge made by the 'ort' strategy.
380f8db (HEAD -> main, origin/styled, styled) HEAD@{2}: checkout: moving from title to main
f0ea621 (origin/title) HEAD@{3}: commit: add title to git-nuestro.md
380f8db (HEAD -> main, origin/styled, styled) HEAD@{4}: checkout: moving from main to title
380f8db (HEAD -> main, origin/styled, styled) HEAD@{5}: merge styled: Fast-forward
e6cf029 HEAD@{6}: checkout: moving from styled to main
380f8db (HEAD -> main, origin/styled, styled) HEAD@{7}: commit (merge): Merge branch 'htmlify' into styled
6081f31 HEAD@{8}: checkout: moving from main to styled
e6cf029 HEAD@{9}: checkout: moving from htmlify to main
a0210c6 (origin/htmlify, htmlify) HEAD@{10}: commit: modify git-nuestro.md in htmlify
e6cf029 HEAD@{11}: checkout: moving from main to htmlify
e6cf029 HEAD@{12}: checkout: moving from styled to main
6081f31 HEAD@{13}: reset: moving to 6081f31
e6cf029 HEAD@{14}: reset: moving to HEAD~1
6081f31 HEAD@{15}: commit: modify git-nuestro.md in styled
e6cf029 HEAD@{16}: checkout: moving from main to styled
e6cf029 HEAD@{17}: commit (initial): add file git-nuestro.md

y luego: git reset --hard 1ae1cab












32) Volver al commit inicial cuando se creó el poema
¿Qué comando o comandos usaste en el paso 32?
git reflog
-- No pongo lo que se ve porque ya lo he puesto en el 30
git reset --hard e6cf029

















33) Volver al estado final, cuando pusimos título al poema
¿Qué comando o comandos usaste en el punto 33?
git reflog
-- No pongo lo que se ve porque ya lo he puesto en el 30
git reset --hard 1ae1cab



