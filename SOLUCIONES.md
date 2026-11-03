# Soluciones de los 23 ejercicios

Los comandos se aplicaron en la copia local del repositorio de [Git Exercises](https://gitexercises.fracz.com/), con el alias `git start` preparado por `./configure.sh`. Tras cada ejercicio se ejecutó `git verify` (en el 23 se verificó el SHA directamente). Todas las pruebas devolvieron **PASSED**.

> `git start <ejercicio>` reinicia los archivos y el historial de esa rama. No lo ejecutes de nuevo sobre las soluciones si quieres conservarlas sin cambios.

## 1. master

```bash
git start master
git verify
```

## 2. commit-one-file

```bash
git start commit-one-file
git add A.txt
git commit -m "Add A file only"
git verify
```

## 3. commit-one-file-staged

```bash
git start commit-one-file-staged
git reset HEAD -- B.txt
git commit -m "Commit only A from staged files"
git verify
```

## 4. ignore-them

Se creó `.gitignore` con estas reglas: `*.exe`, `*.o`, `*.jar` y `libraries/`.

```bash
git add .gitignore
git commit -m "Ignore generated files and libraries"
git verify
```

## 5. chase-branch

```bash
git start chase-branch
git merge --ff-only escaped
git verify
```

## 6. merge-conflict

```bash
git start merge-conflict
git merge another-piece-of-work
# Resolver el conflicto de equation.txt dejando exactamente: 2 + 3 = 5
git add equation.txt
git commit -m "Resolve equation merge conflict"
git verify
```

## 7. save-your-work

```bash
git start save-your-work
git stash push -m "Save work before urgent bugfix"
# Quitar la línea del bug de bug.txt
git add bug.txt
git commit -m "Fix urgent bug"
git stash pop
# Añadir al final de bug.txt: Finally, finished it!
git add bug.txt program.txt
git commit -m "Finish interrupted work"
git verify
```

## 8. change-branch-history

```bash
git start change-branch-history
git rebase hot-bugfix
git verify
```

## 9. remove-ignored

```bash
git start remove-ignored
git rm --cached ignored.txt
git commit -m "Stop tracking ignored file"
git verify
```

## 10. case-sensitive-filename

```bash
git start case-sensitive-filename
git reset --soft HEAD~1
git mv -f File.txt file.txt
git commit -m "Track lowercase file.txt"
git verify
```

## 11. fix-typo

```bash
git start fix-typo
# Reemplazar Hello wordl por Hello world en file.txt
git add file.txt
git commit --amend -m "Add Hello world"
git verify
```

## 12. forge-date

```bash
git start forge-date
GIT_COMMITTER_DATE='1987-08-03T12:00:00 +0000' git commit --amend --no-edit --date='1987-08-03T12:00:00 +0000'
git verify
```

## 13. fix-old-typo

```bash
git start fix-old-typo
git rebase -i HEAD~2
# Marcar edit en el commit "Add Hello wordl"
# Corregir file.txt de wordl a world
git add file.txt
git commit --amend -m "Add Hello world"
git rebase --continue
# Resolver el conflicto conservando las dos líneas correctas de file.txt
git add file.txt
git rebase --continue
git verify
```

## 14. commit-lost

```bash
git start commit-lost
git reflog
# Recuperar el SHA del commit original anterior al amend
git reset --hard a8e431c
git verify
```

## 15. split-commit

```bash
git start split-commit
git reset HEAD~1
git add first.txt
git commit -m "Add first.txt"
git add second.txt
git commit -m "Add second.txt"
git verify
```

## 16. too-many-commits

```bash
git start too-many-commits
git reset --soft HEAD~1
git commit --amend --no-edit
git verify
```

## 17. executable

```bash
git start executable
chmod +x script.sh
git add script.sh
git commit -m "Make script executable"
git verify
```

## 18. commit-parts

Se guardó una copia temporal del `file.txt` completo. Para el primer commit se preparó el contenido solo con las adiciones de la tarea 1; después se restauró el contenido completo y se hizo el segundo commit:

```bash
git start commit-parts
# Preparar file.txt con únicamente los cambios de Task 1
git add file.txt
git commit -m "Finish Task 1 changes"
# Restaurar los cambios restantes en file.txt
git add file.txt
git commit -m "Finish remaining changes (Task 2 and header)"
git verify
```

## 19. pick-your-features

```bash
git start pick-your-features
git cherry-pick feature-a feature-b
# Integrar las dos partes de Feature C en program.txt, conservando A y B
git add program.txt
git commit -m "Implement complete Feature C"
git verify
```

## 20. rebase-complex

```bash
git start rebase-complex
git rebase --onto your-master HEAD~2
git verify
```

## 21. invalid-order

Se rehicieron únicamente los dos últimos commits en el orden correcto:

```bash
git start invalid-order
git reset --hard HEAD~2
git cherry-pick 8f9e49e b85a732
git verify
```

## 22. find-swearwords

Se detectaron los commits que introducían el término buscado en `words.txt` y `list.txt` y se reescribió la historia para sustituirlo por `flower`, sin añadir un commit correctivo al final.

```bash
git start find-swearwords
git log -G'shit' --oneline -- words.txt list.txt
FILTER_BRANCH_SQUELCH_WARNING=1 git filter-branch --force \
  --tree-filter 'for f in words.txt list.txt; do if test -f "$f"; then sed -i "" "s/shit/flower/g" "$f"; fi; done' \
  -- origin/find-swearwords..find-swearwords
git verify
```

## 23. find-bug

Se usó `git bisect` para buscar la primera aparición de `jackass` en el texto codificado con base64. Para `git bisect run`, la prueba devuelve 0 si la versión es buena y 1 si contiene el fallo.

```bash
git start find-bug
git bisect start HEAD 1.0
git bisect run sh -c 'if openssl enc -base64 -A -d < home-screen-text.txt | grep -q jackass; then exit 1; else exit 0; fi'
git bisect reset
git push origin 2e6aac8e8f4c2321306ea6eb6b99d26fbb3ec620:find-bug
```

El servidor contestó **PASSED** para el commit **Change text on home screen #78**. El push es rechazado por el hook del sistema *después* de la verificación, que es el comportamiento normal de esta plataforma.

---

**Progreso comprobado:** [23 de 23 en Git Exercises](https://gitexercises.fracz.com/c/27v).
