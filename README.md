# Git Exercises — 23 de 23 aprobados

Repositorio de entrega de los **23 ejercicios de Git** de [Git Exercises](https://gitexercises.fracz.com/).

**Resultado:** todos los ejercicios han sido resueltos en local en macOS y verificados por el servidor de ejercicios. La verificación oficial muestra **23/23** aprobados.

- [Progreso oficial del verificador](https://gitexercises.fracz.com/c/27v)
- [Comandos y explicación de las soluciones](SOLUCIONES.md)
- [Registro de verificación](PROGRESO.txt)

## Cómo revisar la entrega

La rama `main` contiene la documentación. **Cada ejercicio tiene su propia rama** con el historial resultante de la resolución: puedes abrirla desde el índice inferior y consultar sus commits con `git log`.

La rama `found-first-bug` conserva el commit exacto encontrado mediante `git bisect` para el último ejercicio. Las ramas auxiliares, como `feature-a`, `feature-b` o `your-master`, forman parte de los escenarios originales.

## Índice de los 23 ejercicios

| N.º | Rama de solución | Qué se trabaja | Verificación |
|---:|---|---|---|
| 1 | [`master`](https://github.com/carmelojose309/git-exercises-23/tree/master) | Primer commit y verificación | ✅ Aprobado |
| 2 | [`commit-one-file`](https://github.com/carmelojose309/git-exercises-23/tree/commit-one-file) | Commit de un solo archivo | ✅ Aprobado |
| 3 | [`commit-one-file-staged`](https://github.com/carmelojose309/git-exercises-23/tree/commit-one-file-staged) | Retirar un archivo del staging | ✅ Aprobado |
| 4 | [`ignore-them`](https://github.com/carmelojose309/git-exercises-23/tree/ignore-them) | Reglas de .gitignore | ✅ Aprobado |
| 5 | [`chase-branch`](https://github.com/carmelojose309/git-exercises-23/tree/chase-branch) | Avanzar una rama | ✅ Aprobado |
| 6 | [`merge-conflict`](https://github.com/carmelojose309/git-exercises-23/tree/merge-conflict) | Resolver conflicto de merge | ✅ Aprobado |
| 7 | [`save-your-work`](https://github.com/carmelojose309/git-exercises-23/tree/save-your-work) | Guardar cambios con stash | ✅ Aprobado |
| 8 | [`change-branch-history`](https://github.com/carmelojose309/git-exercises-23/tree/change-branch-history) | Reorganizar mediante rebase | ✅ Aprobado |
| 9 | [`remove-ignored`](https://github.com/carmelojose309/git-exercises-23/tree/remove-ignored) | Dejar de seguir un archivo ignorado | ✅ Aprobado |
| 10 | [`case-sensitive-filename`](https://github.com/carmelojose309/git-exercises-23/tree/case-sensitive-filename) | Corregir mayúsculas en un nombre | ✅ Aprobado |
| 11 | [`fix-typo`](https://github.com/carmelojose309/git-exercises-23/tree/fix-typo) | Corregir último commit | ✅ Aprobado |
| 12 | [`forge-date`](https://github.com/carmelojose309/git-exercises-23/tree/forge-date) | Modificar fecha de un commit | ✅ Aprobado |
| 13 | [`fix-old-typo`](https://github.com/carmelojose309/git-exercises-23/tree/fix-old-typo) | Corregir un commit antiguo | ✅ Aprobado |
| 14 | [`commit-lost`](https://github.com/carmelojose309/git-exercises-23/tree/commit-lost) | Recuperar commit con reflog | ✅ Aprobado |
| 15 | [`split-commit`](https://github.com/carmelojose309/git-exercises-23/tree/split-commit) | Dividir un commit en dos | ✅ Aprobado |
| 16 | [`too-many-commits`](https://github.com/carmelojose309/git-exercises-23/tree/too-many-commits) | Unir commits | ✅ Aprobado |
| 17 | [`executable`](https://github.com/carmelojose309/git-exercises-23/tree/executable) | Activar permiso de ejecución | ✅ Aprobado |
| 18 | [`commit-parts`](https://github.com/carmelojose309/git-exercises-23/tree/commit-parts) | Separar cambios de un archivo | ✅ Aprobado |
| 19 | [`pick-your-features`](https://github.com/carmelojose309/git-exercises-23/tree/pick-your-features) | Integrar tres funcionalidades | ✅ Aprobado |
| 20 | [`rebase-complex`](https://github.com/carmelojose309/git-exercises-23/tree/rebase-complex) | Rebase --onto | ✅ Aprobado |
| 21 | [`invalid-order`](https://github.com/carmelojose309/git-exercises-23/tree/invalid-order) | Invertir orden de commits | ✅ Aprobado |
| 22 | [`find-swearwords`](https://github.com/carmelojose309/git-exercises-23/tree/find-swearwords) | Limpiar palabras del historial | ✅ Aprobado |
| 23 | [`find-bug`](https://github.com/carmelojose309/git-exercises-23/tree/find-bug) | Encontrar primer commit defectuoso | ✅ Aprobado |

## Resultado del último ejercicio

Con `git bisect` se localizó el primer commit que introdujo la palabra problemática en el mensaje codificado de la pantalla inicial:

`2e6aac8e8f4c2321306ea6eb6b99d26fbb3ec620` — **Change text on home screen #78**.

Se comprobó que el commit padre no contiene la palabra y que el identificado sí. Se envió al verificador y obtuvo **PASSED**.

## Nota sobre Git Exercises

La plataforma comprueba el trabajo al intentar hacer `git push` a su propio repositorio: el hook remoto muestra **PASSED** aunque rechace almacenar el push. Esto es el funcionamiento normal del sistema. Esta entrega conserva los historiales en GitHub, independientemente del verificador.
