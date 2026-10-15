# Lab 2 - Preguntas de comprobación

## 1. ¿Por qué un Issue sin criterios de aceptación es un problema, aunque la descripción general parezca clara?

Porque no queda definido exactamente cuándo se considera terminado el trabajo. Los criterios de aceptación permiten comprobar de forma objetiva que se han cumplido todos los requisitos y evitan interpretaciones diferentes entre el autor y el revisor.

## 2. Explica la diferencia entre "Refs #N" y "Closes #N" en un mensaje de commit o en la descripción de un Pull Request.

`Refs #N` simplemente relaciona el commit o Pull Request con un Issue, pero no lo cierra. En cambio, `Closes #N` permite que GitHub cierre automáticamente el Issue cuando los cambios se integran en la rama principal.

## 3. ¿Qué ocurre exactamente si intentas hacer git push directamente sobre una branch main protegida? ¿Es un error tuyo o un fallo del sistema?

GitHub rechaza el push porque la protección de `main` exige integrar los cambios mediante un Pull Request. No es un fallo del sistema, sino que las reglas de seguridad están funcionando correctamente.

## 4. Un compañero te dice: "he aprobado el PR sin mirar los archivos, total ya me fío". ¿Qué riesgo tiene esa forma de revisar?

Se pueden integrar errores, vulnerabilidades o cambios que no cumplen los requisitos. La revisión debe comprobar los archivos modificados y los criterios de aceptación, independientemente de la confianza que tengamos en el autor.

## 5. Si el reviewer pide un cambio y tú ya habías hecho push de tu branch, ¿tienes que abrir un Pull Request nuevo? Explica qué ocurre técnicamente con el PR existente cuando haces un nuevo commit.

No es necesario crear otro Pull Request. Simplemente realizamos las correcciones en la misma rama, hacemos commit y push. GitHub actualiza automáticamente el PR existente con los nuevos commits, manteniendo las revisiones y conversaciones anteriores.

## 6. Describe con tus palabras la diferencia entre Merge commit, Squash and merge y Rebase and merge. ¿Cuál usarías para una branch con commits "wip", "fix", "fix2", "ok ya"?

- **Merge commit:** conserva todos los commits originales y añade uno de fusión.
- **Squash and merge:** combina todos los commits en uno solo.
- **Rebase and merge:** reaplica los commits individualmente sobre `main`, manteniendo un historial lineal.

En este caso utilizaría **Squash and merge**, porque esos commits intermedios no aportan información relevante y es preferible mantener un historial limpio.

## 7. ¿Por qué borrar una branch después del merge no elimina el trabajo realizado en ella?

Porque los cambios ya se han integrado en `main`. Al borrar la branch únicamente eliminamos la referencia a esa rama, pero el trabajo permanece en la rama principal.

## 8. ¿Qué información debería contener siempre la descripción de un Pull Request, como mínimo?

Debe incluir un resumen de lo realizado (Summary), los archivos o elementos modificados (Changes), cómo se han probado los cambios (Testing) y el Issue relacionado (Related Issue).

Además, las pruebas deben indicar cómo verificar los cambios para que el revisor pueda comprobar que funcionan correctamente y cumplen los requisitos.

## 9. Un reviewer escribe solo "esto está mal" como comentario. ¿Qué le falta a ese comentario para ser útil? Reescríbelo tú con un ejemplo inventado.

Le falta explicar cuál es el problema, por qué es importante y cómo podría solucionarse.

Por ejemplo: `issue (blocking): El enlace a CONTRIBUTING.md en el README apunta a una ruta incorrecta. Hay que corregirlo para que los usuarios puedan acceder a la documentación.`

## 10. ¿Qué diferencia hay entre que main esté protegida y que simplemente el equipo "se ponga de acuerdo" en no hacer push directo?

Si únicamente existe un acuerdo, cualquier desarrollador podría saltárselo accidentalmente. En cambio, al proteger `main`, GitHub aplica las restricciones automáticamente y exige cumplir las condiciones configuradas antes de integrar cambios.

## 11. Explica con un ejemplo propio la diferencia entre un comentario issue: (blocking) y uno nitpick: (if-minor) en formato Conventional Comments.

`issue (blocking)`: indica un problema importante que debe solucionarse antes de aprobar el cambio.



`nitpick (if-minor)`: señala un detalle menor que no debería impedir la aprobación.

Ejemplo: `nitpick (if-minor): Cambiaría el nombre de esta variable para que sea más descriptivo.`

## 12. Si tu próximo commit es feat!: cambia la firma de la función principal de la API, ¿qué tipo de versión SemVer se dispara y por qué?

Se produce un incremento **MAJOR**, por ejemplo, de `2.1.0` a `3.0.0`. El símbolo `!` indica un *breaking change*, es decir, un cambio que rompe la compatibilidad con versiones anteriores de la API.

## 13. ¿Por qué abrir un Draft PR desde el primer commit estructural puede ahorrar tiempo al equipo, aunque parezca más lento para el autor individual?

Porque permite que otros desarrolladores revisen el enfoque inicial antes de invertir demasiado tiempo en implementarlo. Si existe algún problema de diseño, se detecta pronto y se evitan correcciones o refactorizaciones importantes cuando el trabajo ya está avanzado.