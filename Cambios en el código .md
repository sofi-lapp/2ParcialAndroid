# Cambios en el código

**`Programa.kt` seria de la liena 20 a la 43.**

 Antes al actualizar el programa, la app borraba todas las charlas y las volvía a cargar por eso las estrellas de las favoritas se perdían. Ahora con el metodo nuevo `sincronizar()`, hace todo junto. Anota que charlas estaban marcadas, saca las que ya no están en el programa y guarda las nuevas manteniendo esas marcas. Si una charla cambia de título o sala, sigue marcada. 

Si desaparece y después vuelve, vuelve sin marcar.

**`AgendaRepository.kt` seria de la liena 3 a la 20.**

 Cuando el programa se descarga bien, la app anota que ya tiene una edición. Hace falta porque un programa vacío (la v4) es válido, pero sin esa nota se vería igual que no haber descargado nada, y la app no sabría si mostrar *Sin charlas programadas* o el botón de reintentar.

**`ProgramaModel.kt` seria de la liena  11 a la 32.**

 Controla las descargas. Hace una sola descarga automática al abrir la app, mientras hay una en curso, ignora los nuevos pedidos. Así, dos toques seguidos en “Actualizar” suman un solo intento,también calcula si hay un programa guardado, para decidir qué mensaje mostrar cuando falla la conexión.

**`Servicios.kt` líneas 12 a 27.** 

Antes, cada vez que se recreaba la pantalla se armaba todo de cero, con el contador en cero y la carga automática como nueva. Ahora existe una sola copia mientras la app esté viva en el celular y el contador y la carga automática duran toda la sesión.

**`MainActivity.kt` línea 22.**

 Antes, al girar el celular o volver desde otra app, se disparaba una descarga cada vez. Ahora esa línea pide la “carga inicial”, que el modelo solo permite una vez.

**`Catalogo.kt` líneas 15 a 35.**

 Cambia lo que ve el usuario cuando algo falla. Si no hay internet y ya había datos, la lista sigue visible con el aviso de que se están usando datos guardados. Si no había nada guardado, aparece el botón “Reintentar”. Si el programa es válido pero viene vacío, dice “Sin charlas programadas”. También eliminé la recarga que se disparaba al volver a la pestaña o salir de una charla.

**`Portada.kt` en las líneas 19, 20 y 54.**

 Los filtros de día y tema ahora se guardan en esta pantalla, que no desaparece al abrir una charla. Por eso no se pierden al volver, al girar el celular ni cuando Android cierra la app en segundo plano, y recién se borran cuando se abre la app desde cero.