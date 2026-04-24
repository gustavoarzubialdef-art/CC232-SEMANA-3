#### Bloque 1 - Núcleo conceptual de la semana

Revisen:

- `Semana3/README.md`
- `Parte3-Deng.docx`
- `Parte3-Morin.docx`
- `Semana3/include/SLList.h`
- `Semana3/include/DLList.h`
- `Semana3/include/SEList.h`
- `Semana3/include/DengList.h`
- `Semana3/include/MorinDengBridge.h`

Respondan:

1. Expliquen con sus palabras qué cambia cuando una estructura pasa de almacenamiento contiguo a almacenamiento dinámico.
La memoria ya no es un bloque único sino nodos dispersos conectados por punteros.

2. Expliquen la diferencia entre acceso por rango y acceso por posición o enlace.


3. Expliquen por qué una lista enlazada mejora inserciones y eliminaciones locales, pero empeora el acceso por índice.
4. Expliquen por qué `SLList` implementa bien operaciones de `Stack` y `Queue`.
5. Expliquen por qué `SLList` no implementa naturalmente todas las operaciones de un `Deque` con el mismo costo.
6. Expliquen qué aporta el nodo centinela `dummy` en `DLList`.
7. Expliquen por qué `DLList` permite justificar `get(i)`, `set(i,x)`, `add(i,x)` y `remove(i)` con costo `O(1 + min(i, n-i))`.
8. Expliquen cuál es la idea espacial central de `SEList`.
9. Expliquen por qué `SEList` reutiliza una `BDeque` basada en `ArrayDeque`.
10. Expliquen qué papel cumple `DengList` dentro de esta semana y por qué no reemplaza a las estructuras de Morin.

#### Bloque 2 - Demostración y trazado guiado

Revisen:

- `Semana3/demos/demo_sllist.cpp`
- `Semana3/demos/demo_dllist.cpp`
- `Semana3/demos/demo_selist.cpp`
- `Semana3/demos/demo_deng_list.cpp`
- `Semana3/demos/demo_morin_deng_bridge.cpp`
- `Semana3/demos/demo_capitulo3_panorama.cpp`
- `Semana3/demos/demo_min_structures.cpp`
- `Semana3/demos/demo_xor_list.cpp`
- `Semana3/demos/demo_linked_adapters.cpp`
- `Semana3/demos/demo_contiguous_vs_linked.cpp`

Construyan una tabla con cuatro columnas:

- Archivo
- Salida u observable importante
- Idea estructural
- Argumento de costo, espacio o diseño

Luego respondan:

1. En `demo_sllist.cpp`, ¿qué secuencia deja más clara la coexistencia de comportamiento tipo pila y tipo cola dentro de `SLList`?
Pila: push(5) inserta al inicio, pop() remueve del inicio. La lista actúa como LIFO (Last In, First Out).
Cola: add(10) y add(20) insertan al final, remove() remueve del inicio. La lista actúa como FIFO (First In, First Out).
Coexistencia: Ambas operaciones comparten el mismo extremo (el frente) para acceso/remoción, pero usan extremos opuestos para inserción.
Esto demuestra cómo SLList puede simular ambas estructuras.

2. En `demo_dllist.cpp`, ¿qué operación muestra mejor la inserción en una posición intermedia?
add(1, 20) inserta el valor 20 en la posición índice 1, desplazando el elemento existente (30) hacia la derecha.
La lista queda como [10, 20, 30], demostrando cómo DLList permite inserciones eficientes en posiciones arbitrarias sin necesidad de desplazar todos los elementos

3. En `demo_selist.cpp`, ¿qué observable permite defender que la lista mantiene orden lógico aunque internamente trabaje por bloques?
4. En `demo_deng_list.cpp`, ¿qué evidencia muestra que la lista reforzada por Deng ofrece operaciones más cercanas a un ADT de lista completo?
5. En `demo_morin_deng_bridge.cpp`, ¿qué parte de la salida permite justificar que se reutilizan algoritmos sin reescribir la estructura base?
6. En `demo_min_structures.cpp`, ¿qué diferencia conceptual observan entre almacenar valores y almacenar información adicional para responder `min()`?
7. En `demo_linked_adapters.cpp`, ¿qué adaptador representa mejor la idea de reutilizar una estructura existente para ofrecer una interfaz nueva?
8. En `demo_contiguous_vs_linked.cpp`, ¿qué contraste se observa entre acceso por índice, inserción local y localidad de memoria?

#### Bloque 3 - Pruebas públicas, stress y correctitud

Revisen:

- `Semana3/pruebas_publicas/README.md`
- `Semana3/pruebas_publicas/test_public_week3.cpp`
- `Semana3/pruebas_publicas/test_public_deng_bridge.cpp`
- `Semana3/pruebas_publicas/test_public_extras.cpp`
- `Semana3/pruebas_publicas/test_public_linked_adapters.cpp`
- `Semana3/pruebas_publicas/test_public_contiguous_vs_linked.cpp`
- `Semana3/pruebas_internas/test_internal_week3.cpp`
- `Semana3/pruebas_internas/test_internal_deng_algorithms.cpp`
- `Semana3/pruebas_internas/test_internal_extras.cpp`
- `Semana3/pruebas_internas/stress_selist_week3.cpp`

Respondan:

1. ¿Qué operaciones mínimas valida la prueba pública para `SLList`?
- add(int i, const T& x): Inserción en posiciones específicas (índices 0, 1, 1).
- get(int i): Acceso por índice para verificar elementos.
- remove(int i): Eliminación por índice.
- size(): Consulta del tamaño de la lista.

2. ¿Qué operaciones mínimas valida la prueba pública para `DLList`?
3. ¿Qué operaciones mínimas valida la prueba pública para `SEList`?
4. ¿Qué operaciones nuevas quedan cubiertas por `test_public_extras.cpp`?
5. ¿Qué valida específicamente `test_public_linked_adapters.cpp` sobre `LinkedStack`, `LinkedQueue` y `LinkedDeque`?
6. ¿Qué demuestra `test_public_deng_bridge.cpp` sobre integración y reutilización?
7. En `stress_selist_week3.cpp`, ¿qué comportamiento intenta estresar sobre crecimiento, borrado y mantenimiento del tamaño lógico?
8. ¿Qué sí demuestra una prueba pública sobre una estructura enlazada?
9. ¿Qué no demuestra una prueba pública por sí sola?
10. ¿Por qué pasar pruebas no reemplaza una explicación de invariantes, punteros y complejidad?

#### Bloque 4 - SLList, DLList y SEList: lectura cercana del código

Revisen:

- `Semana3/include/SLList.h`
- `Semana3/include/DLList.h`
- `Semana3/include/SEList.h`
- `Parte3-Morin.docx`
- `Parte3-Deng.docx`

Respondan:

1. En `SLList`, ¿qué papel cumplen `head`, `tail` y `n`?
2. En `SLList::push`, `pop`, `add` y `remove`, ¿qué punteros cambian exactamente?
3. Expliquen cómo funciona `secondLast()` y por qué no puede resolverse directamente con solo mirar `tail`.
4. Expliquen paso a paso cómo funciona `reverse()` y por qué no necesita estructura auxiliar.
5. Expliquen qué verifica `checkSize()` y por qué esta función ayuda a defender correctitud.
6. En `DLList`, expliquen por qué `getNode(i)` puede empezar desde el inicio o desde el final.
7. En `DLList::addBefore`, ¿qué enlaces se actualizan y por qué el nodo centinela elimina casos borde?
8. Expliquen cómo funciona `rotate(r)` sin mover los datos elemento por elemento.
9. Expliquen cómo `isPalindrome()` aprovecha la naturaleza doblemente enlazada de la estructura.
10. En `SEList`, expliquen qué representa `Location`.
11. Expliquen qué hacen `spread()` y `gather()` y en qué situaciones aparecen.
12. Expliquen cómo el tamaño de bloque `b` afecta compromiso entre acceso, actualización y uso de espacio.

#### Bloque 5 - Adaptadores y estructuras derivadas

Revisen:

- `Semana3/include/LinkedStack.h`
- `Semana3/include/LinkedQueue.h`
- `Semana3/include/LinkedDeque.h`
- `Semana3/include/MinStack.h`
- `Semana3/include/MinQueue.h`
- `Semana3/include/MinDeque.h`
- `Semana3/demos/demo_linked_adapters.cpp`
- `Semana3/demos/demo_min_structures.cpp`

Respondan:

1. ¿Cómo reutiliza `LinkedStack` a `SLList`?
2. ¿Cómo reutiliza `LinkedQueue` a `SLList`?
3. ¿Por qué `LinkedDeque` se construye naturalmente sobre `DLList` y no sobre `SLList`?
4. En `MinStack`, ¿por qué cada entrada guarda el valor y el mínimo acumulado?
5. En `MinQueue`, ¿por qué usar dos pilas permite mantener semántica FIFO y consulta de mínimo?
6. En `MinDeque`, ¿qué problema resuelve el rebalanceo entre `front_` y `back_`?
7. Comparen "implementar una estructura" y "adaptar una estructura existente" usando ejemplos de este bloque.
8. ¿Qué operaciones pueden defender como constantes y cuáles deben defender como amortizadas?

#### Bloque 6 - Deng como refuerzo algorítmico y puente de integración

Revisen:

- `Semana3/include/CleanList.h`
- `Semana3/include/DengList.h`
- `Semana3/include/MorinDengBridge.h`
- `Semana3/demos/demo_deng_list.cpp`
- `Semana3/demos/demo_morin_deng_bridge.cpp`
- `Semana3/pruebas_publicas/test_public_deng_bridge.cpp`
- `Semana3/pruebas_internas/test_internal_deng_algorithms.cpp`
- `Parte3-Deng.docx`

Respondan:

1. ¿Qué operaciones del ADT de lista aparecen reforzadas en `DengList`?
2. ¿Qué ventaja tiene encapsular una lista más rica sin cambiar el resto de estructuras de Semana 3?
3. Expliquen qué hacen `to_deng` y `assign_from_deng`.
4. Expliquen por qué `stable_sort_with_deng` no obliga a reimplementar ordenamiento dentro de `DLList` o `SEList`.
5. Expliquen qué hace `dedup_with_deng` y qué relación guarda con `deduplicate()` o `uniquify()` de la teoría.
6. Expliquen por qué `reverse_with_deng` es un ejemplo de reutilización de algoritmos sobre una interfaz común.
7. ¿Qué costo adicional introduce la conversión entre estructuras y cuándo vale la pena aceptarlo?

#### Bloque 7 - Comparación enlazado vs contiguo, variantes y evidencia experimental

Revisen:

- `Semana3/include/ArrayDeque.h`
- `Semana3/include/XorList.h`
- `Semana3/demos/demo_contiguous_vs_linked.cpp`
- `Semana3/demos/demo_xor_list.cpp`
- `Semana3/benchmarks/benchmark_semana3.cpp`
- `Parte3-Morin.docx`

Respondan:

1. Comparen `ArrayDeque` y `LinkedDeque`: ¿qué cambia en representación y qué cambia en costo observable?
2. ¿Qué significa que una representación contigua tenga mejor localidad de memoria?
3. ¿Qué tipo de operaciones favorecen más a la representación enlazada?
4. En el benchmark, ¿qué comparación sirve mejor para discutir acceso aleatorio y cuál sirve mejor para discutir operaciones en extremos?
5. ¿Por qué el benchmark no debe leerse como prueba absoluta de superioridad de una estructura sobre otra?
6. ¿Qué idea intenta mostrar `XorList` respecto al ahorro de punteros?
7. ¿Qué desventaja práctica introduce una estructura como `XorList` aunque sea interesante desde el punto de vista del espacio?.

#### Bloque 8 - Cierre comparativo y preparación de sustentación

Respondan esta pregunta final:

¿Qué cambia cuando pasamos de "usar arreglos dinámicos" a "diseñar estructuras enlazadas y adaptadores sobre nodos"?

La respuesta debe incluir obligatoriamente:

- Una afirmación sobre representación
- Una afirmación sobre acceso por rango frente a acceso por posición
- Una afirmación sobre inserciones y eliminaciones locales
- Una afirmación sobre complejidad de `SLList`, `DLList` y `SEList`
- Una afirmación sobre reutilización mediante adaptadores o puentes
- Una comparación entre representación contigua y enlazada.
