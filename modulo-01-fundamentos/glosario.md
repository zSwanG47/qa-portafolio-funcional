# Glosario · Módulo 1. Fundamentos del testing

Glosario personal de 35 términos del [Módulo 1](../README.md#módulo-1-fundamentos-del-testing), según ISTQB CTFL v4.0. Cada definición está en lenguaje sencillo y el ejemplo usa [SauceDemo](https://www.saucedemo.com) cuando el concepto encaja en esa tienda.

## Índice de términos

1. [Testing](#1-testing)
2. [Debugging](#2-debugging-depuración)
3. [Error](#3-error)
4. [Defecto](#4-defecto-bug)
5. [Falla](#5-falla)
6. [Causa raíz](#6-causa-raíz)
7. [QA](#7-qa-quality-assurance)
8. [QC](#8-qc-quality-control)
9. [Paradoja del pesticida](#9-paradoja-del-pesticida)
10. [Agrupación de defectos](#10-agrupación-de-defectos)
11. [Shift-left](#11-shift-left)
12. [Falacia de la ausencia de defectos](#12-falacia-de-la-ausencia-de-defectos)
13. [Pruebas exhaustivas](#13-pruebas-exhaustivas)
14. [Proceso de pruebas](#14-proceso-de-pruebas)
15. [Base de prueba](#15-base-de-prueba)
16. [Testware](#16-testware)
17. [Condición de prueba](#17-condición-de-prueba)
18. [Caso de prueba](#18-caso-de-prueba)
19. [Prueba de componente](#19-prueba-de-componente-unitaria)
20. [Integración de componentes](#20-integración-de-componentes)
21. [Prueba de sistema](#21-prueba-de-sistema)
22. [Integración de sistemas](#22-integración-de-sistemas)
23. [Prueba de aceptación / UAT](#23-prueba-de-aceptación-uat)
24. [Pruebas alfa y beta](#24-pruebas-alfa-y-beta)
25. [Prueba funcional](#25-prueba-funcional)
26. [Prueba no funcional](#26-prueba-no-funcional)
27. [Caja negra](#27-caja-negra)
28. [Caja blanca](#28-caja-blanca)
29. [Retest](#29-retest-prueba-de-confirmación)
30. [Prueba de regresión](#30-prueba-de-regresión)
31. [Smoke test](#31-smoke-test)
32. [Sanity test](#32-sanity-test)
33. [Pruebas estáticas y dinámicas](#33-pruebas-estáticas-y-dinámicas)
34. [Modelos de desarrollo](#34-modelos-de-desarrollo-cascada-modelo-en-v-y-ágil)
35. [Verificación y validación](#35-verificación-y-validación)

---

### 1. Testing

**Definición:** Conjunto de actividades para evaluar la calidad de un software y reducir el riesgo de que falle en producción. No se limita a ejecutar pruebas: también incluye analizar qué probar, diseñar casos, preparar datos, reportar resultados y cerrar el ciclo.

**Ejemplo:** En SauceDemo, testing es revisar el login, el inventario, el carrito y el checkout para comprobar que un cliente puede completar una compra.

### 2. Debugging (depuración)

**Definición:** Actividad del desarrollador para localizar, analizar y corregir la causa de un defecto. El testing encuentra la falla y deja evidencia; el debugging la repara. Después, el QA hace el retest.

**Ejemplo:** Si el checkout de SauceDemo rechazara un código postal válido, el QA reportaría la falla y el desarrollador depuraría la validación del campo Zip hasta corregirla.

### 3. Error

**Definición:** Equivocación humana que produce un resultado incorrecto. Puede ocurrir al escribir código, al redactar un requisito o al cargar datos.

**Ejemplo:** Alguien carga el catálogo de SauceDemo y escribe un nombre de prueba en lugar del nombre comercial del producto.

### 4. Defecto (bug)

**Definición:** Imperfección que queda en el código, en los datos o en un documento a causa de un error. Puede existir sin que nadie lo haya visto todavía, si esa parte no se ejecuta o no se dan las condiciones.

**Ejemplo:** En los datos del catálogo de SauceDemo, un producto quedó guardado como `Test.allTheThings() T-Shirt (Red)`.

### 5. Falla

**Definición:** Comportamiento observable distinto al esperado cuando se ejecuta el defecto. Es lo que el QA ve en pantalla y reporta.

**Ejemplo:** En la tienda, el usuario ve ese texto técnico como título del producto, en lugar de un nombre claro.

### 6. Causa raíz

**Definición:** El motivo de fondo que originó el error, más allá del síntoma. Si solo se corrige el defecto y no la causa raíz, el problema suele volver a aparecer.

**Ejemplo:** Si un nombre de prueba llegó al catálogo de SauceDemo, la causa raíz puede ser que nadie revisó los datos de los productos antes de publicarlos.

### 7. QA (Quality Assurance)

**Definición:** Aseguramiento de la calidad. Enfoque preventivo sobre el proceso: busca que el equipo trabaje de un modo que se introduzcan menos defectos, con estándares, revisiones y buenas prácticas.

**Ejemplo:** Acordar, antes de programar el checkout de SauceDemo, que cada historia tenga criterios de aceptación claros y que los textos del catálogo se revisen antes de publicarlos.

### 8. QC (Quality Control)

**Definición:** Control de la calidad. Enfoque correctivo sobre el producto: verifica que lo construido cumpla lo pedido. El testing es la actividad principal de QC.

**Ejemplo:** Ejecutar en SauceDemo el flujo de compra y comprobar que, al pulsar Finish, aparece el mensaje "Thank you for your order!".

### 9. Paradoja del pesticida

**Definición:** Si se repiten siempre las mismas pruebas, dejan de encontrar defectos nuevos, igual que un pesticida pierde efecto. Hay que revisar y actualizar los casos, agregar datos y escenarios, y combinarlos con pruebas exploratorias.

**Ejemplo:** Si en SauceDemo solo pruebo el login de `standard_user`, no voy a detectar que `locked_out_user` debe ver un mensaje de bloqueo. Por eso sumo otros usuarios, datos y recorridos.

### 10. Agrupación de defectos

**Definición:** Un número pequeño de módulos suele concentrar la mayoría de los defectos (principio de Pareto). Conviene invertir más esfuerzo de prueba donde ya se han visto más problemas.

**Ejemplo:** Si en SauceDemo la mayoría de fallos aparecen en el checkout (First Name, Last Name y Zip), priorizo esa zona frente a pantallas más estables, como el logout.

### 11. Shift-left

**Definición:** Mover las actividades de calidad lo más temprano posible en el ciclo. Un defecto encontrado en el requisito es mucho más barato de corregir que uno encontrado en producción. El testing también depende del contexto: no se prueba igual una tienda de demostración que una app bancaria.

**Ejemplo:** Revisar los criterios de aceptación del carrito de SauceDemo en el refinamiento, antes de desarrollar la pantalla, en lugar de esperar a probarla cuando ya está terminada.

### 12. Falacia de la ausencia de defectos

**Definición:** Creer que un sistema sin bugs conocidos ya es de calidad. Un producto puede no fallar y aun así ser inútil si no resuelve lo que el usuario necesita. El testing puede mostrar que hay defectos, nunca garantizar que no existan.

**Ejemplo:** SauceDemo podría completar el checkout sin errores técnicos y, aun así, no servir si el comprador no entiende cómo pagar o si el nombre del producto no describe lo que está comprando.

### 13. Pruebas exhaustivas

**Definición:** Probar todas las combinaciones de datos, rutas y ambientes es imposible. Por eso se usan técnicas de diseño y se prioriza por riesgo: primero lo que más impacta al negocio y lo que más probabilidad tiene de fallar.

**Ejemplo:** En el checkout de SauceDemo no puedo probar todos los nombres, apellidos y códigos postales posibles. Elijo casos representativos (válidos, vacíos e inválidos) y me centro en lo que bloquea la compra.

### 14. Proceso de pruebas

**Definición:** ISTQB agrupa el trabajo de testing en siete actividades, que se adaptan a cada proyecto (en ágil ocurren en cada sprint):

| Actividad | Qué se hace | Producto (testware) |
| --- | --- | --- |
| Planificación | Definir objetivos, alcance, enfoque, recursos y cronograma | Plan de pruebas |
| Monitoreo y control | Comparar el avance real con el plan y tomar acciones | Informes de avance |
| Análisis | Revisar la base de prueba y decidir qué probar | Condiciones de prueba |
| Diseño | Decidir cómo probar: casos y datos | Casos de prueba |
| Implementación | Preparar datos, ambientes, scripts y suites | Suites, datos y scripts |
| Ejecución | Correr las pruebas, comparar resultados y reportar defectos | Resultados y reportes de bugs |
| Cierre | Recoger lecciones, archivar el testware y emitir el informe final | Informe de cierre |

**Ejemplo:** Para SauceDemo, planifico cubrir login, inventario, carrito y checkout; analizo qué debe cumplir cada flujo; diseño los casos; los ejecuto con `standard_user`; y dejo documentados los resultados al cerrar.

### 15. Base de prueba

**Definición:** Todo lo que se usa para saber qué debe hacer el sistema: historias de usuario, criterios de aceptación, documentos funcionales, prototipos, reglas de negocio o contratos de API.

**Ejemplo:** Para probar SauceDemo, la base de prueba es el comportamiento visible de la tienda: un usuario válido entra, ve productos, arma el carrito y termina la compra con First Name, Last Name y Zip.

### 16. Testware

**Definición:** Todos los productos que genera o utiliza el proceso de pruebas: planes, casos, scripts, datos, suites, informes y reportes de defectos.

**Ejemplo:** Este repositorio es testware: el glosario, el mapa de niveles y los ejemplos documentados de SauceDemo.

### 17. Condición de prueba

**Definición:** Un aspecto concreto que se decide probar, derivado de la base de prueba. Es el "qué" hay que cubrir, todavía no el paso a paso.

**Ejemplo:** "Un usuario válido debe poder iniciar sesión en SauceDemo" es una condición de prueba. Aún no indica qué usuario escribir ni qué botón pulsar.

### 18. Caso de prueba

**Definición:** Especificación de cómo comprobar una o más condiciones de prueba: precondiciones, pasos, datos de entrada y resultado esperado.

**Ejemplo:** Precondición: estar en saucedemo.com. Pasos: ingresar `standard_user` y `secret_sauce`, y pulsar Login. Resultado esperado: se muestra el inventario de productos.

### 19. Prueba de componente (unitaria)

**Definición:** Nivel que prueba una unidad aislada (método, clase o función), por lo general con caja blanca. La ejecuta el desarrollador.

**Ejemplo:** Si el equipo tuviera tests unitarios del cálculo del carrito, un caso comprobaría que 29.99 + 9.99 = 39.98, sin abrir el navegador. En la práctica de este módulo trabajo sobre la UI pública de SauceDemo, no sobre su código interno.

### 20. Integración de componentes

**Definición:** Nivel que comprueba la interacción entre partes de un mismo sistema, por ejemplo la pantalla y la lógica del carrito. Lo suelen ejecutar el desarrollador o el QA.

**Ejemplo:** En SauceDemo, pulsar Add to cart en un producto y verificar que el contador del carrito y la lista en Your Cart se actualizan de forma coherente.

### 21. Prueba de sistema

**Definición:** Nivel que evalúa el sistema completo, de punta a punta, contra los requisitos. Normalmente lo ejecuta QA, con enfoque de caja negra.

**Ejemplo:** Recorrer en SauceDemo el flujo completo: login, agregar un producto, checkout con First Name, Last Name y Zip, y Finish, hasta ver "Thank you for your order!".

### 22. Integración de sistemas

**Definición:** Nivel que prueba la interacción con otros sistemas, como APIs externas, pasarelas de pago o un core bancario. Lo suele ejecutar QA.

**Ejemplo:** SauceDemo es una tienda de demostración y no se conecta a una pasarela real. En un sistema equivalente, este nivel comprobaría que al confirmar la orden el pago se registra en el proveedor externo. Aquí me limito a validar el flujo interno hasta el mensaje de confirmación.

### 23. Prueba de aceptación (UAT)

**Definición:** Nivel que comprueba que el sistema sirve al negocio y al usuario. Incluye UAT, pruebas operacionales y contractuales. La ejecutan el usuario, el negocio o QA en apoyo. Se inclina más a la validación que a la verificación.

**Ejemplo:** Un responsable de tienda entra a SauceDemo con `standard_user`, completa una compra como lo haría un cliente y acepta el sistema si llega al mensaje de agradecimiento sin bloqueos.

### 24. Pruebas alfa y beta

**Definición:** Formas de aceptación con usuarios. La prueba alfa se hace en un entorno controlado, todavía en casa del equipo. La prueba beta se hace en el entorno del usuario, con una versión casi lista.

**Ejemplo:** Una alfa de SauceDemo sería que testers internos usen la tienda en el ambiente del equipo. Una beta sería dejar que personas ajenas al equipo la prueben en su propio navegador antes del lanzamiento.

### 25. Prueba funcional

**Definición:** Evalúa qué hace el sistema: reglas de negocio, flujos y cálculos. Responde a la pregunta "¿el sistema hace lo que debe hacer?".

**Ejemplo:** En SauceDemo, agregar Sauce Labs Backpack, ir al carrito y comprobar que el producto y su precio aparecen antes de continuar el checkout.

### 26. Prueba no funcional

**Definición:** Evalúa cómo lo hace el sistema. Según ISO/IEC 25010 incluye, entre otros, rendimiento, seguridad, usabilidad, compatibilidad, fiabilidad, mantenibilidad y portabilidad.

**Ejemplo:** Comparar el tiempo de login de `performance_glitch_user` con el de `standard_user`, que entra sin una demora notable. También encaja una prueba de usabilidad o de compatibilidad si el navegador traduce la página.

### 27. Caja negra

**Definición:** Técnica basada en la especificación, sin mirar el código. Se observan las entradas y las salidas.

**Ejemplo:** Probar el login de SauceDemo con `locked_out_user` y comprobar que el acceso se rechaza, sin revisar cómo está programado el bloqueo.

### 28. Caja blanca

**Definición:** Técnica basada en la estructura interna: código, ramas y caminos. Se usa sobre todo en pruebas de componente.

**Ejemplo:** Si se tuviera el código del validador del checkout, se diseñarían casos para cubrir cada rama: First Name vacío, Last Name vacío y Zip vacío. Desde la UI pública de SauceDemo trabajo principalmente en caja negra.

### 29. Retest (prueba de confirmación)

**Definición:** Volver a ejecutar los mismos pasos de un defecto ya corregido para confirmar que la falla ya no ocurre.

**Ejemplo:** Si se corrigiera el título `Test.allTheThings() T-Shirt (Red)`, volvería al inventario y al detalle del producto para comprobar que ahora muestra un nombre comercial claro.

### 30. Prueba de regresión

**Definición:** Verificar que un cambio o una corrección no rompió algo que ya funcionaba. Se aplica sobre las áreas impactadas o sobre un conjunto estable de casos.

**Ejemplo:** Después de un ajuste en el carrito de SauceDemo, vuelvo a probar login, agregar productos, checkout y logout, aunque esos flujos no fueran el objeto del cambio.

### 31. Smoke test

**Definición:** Prueba rápida y amplia de las funciones críticas, para decidir si el build es estable y se puede seguir probando. Se hace sobre cada nuevo despliegue.

**Ejemplo:** En un build nuevo de SauceDemo: iniciar sesión con `standard_user`, ver el inventario, agregar un producto al carrito y abrir Your Cart. Si algo crítico falla, no continúo con el resto de las pruebas.

### 32. Sanity test

**Definición:** Prueba rápida y enfocada en una funcionalidad que cambió o se corrigió, para confirmar que tiene sentido seguir con pruebas más profundas.

**Ejemplo:** Si se corrigió solo el ordenamiento por precio en SauceDemo, hago un sanity de Price low to high y Price high to low antes de reejecutar todo el catálogo.

### 33. Pruebas estáticas y dinámicas

**Definición:** Las pruebas estáticas evalúan el software o sus documentos sin ejecutarlo: revisión de historias, revisión de código o análisis con herramientas. Las dinámicas ejecutan el software. Los tipos de revisión, de menos a más formal, son: revisión informal, walkthrough (recorrido guiado por el autor), revisión técnica e inspección (la más formal, con roles y métricas).

**Ejemplo:** Un walkthrough de los textos del catálogo de SauceDemo habría podido detectar el nombre de prueba antes de publicarlo (estática). Abrir la tienda y ver el título en pantalla es una prueba dinámica.

### 34. Modelos de desarrollo (cascada, modelo en V y ágil)

**Definición:** El modelo de desarrollo cambia cuándo y cómo se prueba:

- **Cascada:** fases secuenciales; el testing suele llegar al final, cuando corregir es más caro.
- **Modelo en V:** cada fase de desarrollo tiene un nivel de prueba asociado (requisitos con aceptación, diseño con sistema, código con unitarias).
- **Ágil** (iterativo e incremental): entregas cortas; el QA prueba en cada sprint, automatiza la regresión y participa desde el refinamiento.

**Ejemplo:** En un equipo ágil que mantuviera SauceDemo, en cada sprint probaría los cambios del catálogo o del checkout y dejaría una regresión corta de login y compra.

### 35. Verificación y validación

**Definición:** Verificar es preguntarse "¿estamos construyendo el producto correctamente?", es decir, si cumple la especificación. Validar es preguntarse "¿estamos construyendo el producto correcto?", es decir, si resuelve la necesidad del usuario. Las pruebas de sistema se inclinan más a la verificación y la UAT a la validación.

**Ejemplo:** Verificación: el checkout de SauceDemo pide First Name, Last Name y Zip y, al completarlos, permite finalizar. Validación: un comprador entiende el flujo y considera útil el mensaje "Thank you for your order!".
