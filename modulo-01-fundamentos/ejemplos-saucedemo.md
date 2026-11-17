# Ejemplos en SauceDemo

Práctica del Módulo 1 sobre [https://www.saucedemo.com](https://www.saucedemo.com).

- Usuario: `standard_user`
- Contraseña: `secret_sauce` (credencial pública de la demo)
- Alcance: login, inventario, carrito, checkout (First Name, Last Name y Zip), Finish, ordenamiento por precio y menú (Logout / Reset App State)

Los cinco ejemplos siguientes son casos concretos, no una batería completa.

## 1. Prueba funcional

**Objetivo:** Verificar que un usuario autenticado puede completar una compra y que el sistema confirma la orden.

**Pasos:**

1. Abrir https://www.saucedemo.com.
2. Iniciar sesión con `standard_user` / `secret_sauce`.
3. En el inventario, pulsar Add to cart en Sauce Labs Backpack.
4. Abrir el carrito (Your Cart) y comprobar que el producto está en la lista.
5. Pulsar Checkout.
6. Completar First Name, Last Name y Zip/Postal Code con datos válidos, por ejemplo Ana, Perez y 15001.
7. Pulsar Continue y revisar el resumen.
8. Pulsar Finish.

**Resultado esperado:** La compra termina sin errores y la pantalla muestra el mensaje "Thank you for your order!".

## 2. Prueba no funcional

**Objetivo:** Evaluar el rendimiento percibido del login, comparando un usuario estándar con `performance_glitch_user`, que en SauceDemo retrasa el inicio de sesión.

**Pasos:**

1. Abrir https://www.saucedemo.com e iniciar sesión con `standard_user` / `secret_sauce`.
2. Observar que el inventario aparece sin una demora notable y cerrar sesión con Logout.
3. Volver a la pantalla de login e iniciar sesión con `performance_glitch_user` / `secret_sauce`.
4. Observar el tiempo hasta que carga el inventario, en el mismo navegador y en condiciones similares.

**Resultado esperado:** Con `standard_user` el inventario se muestra de forma ágil. Con `performance_glitch_user` el mismo login tarda de manera notable. El caso no juzga una regla de negocio, sino el *cómo* responde la tienda.

Nota: también sería una prueba no funcional de usabilidad o compatibilidad revisar la tienda con la traducción automática del navegador, porque puede alterar textos y el marcado de la página.

## 3. Smoke test

**Objetivo:** Comprobar, de forma rápida y amplia, que las funciones críticas de un build están vivas y que vale la pena seguir probando.

**Pasos:**

1. Abrir https://www.saucedemo.com.
2. Iniciar sesión con `standard_user` / `secret_sauce`.
3. Verificar que el inventario muestra productos.
4. Agregar un producto al carrito y abrir Your Cart.
5. Pulsar Checkout y confirmar que aparecen los campos First Name, Last Name y Zip.
6. Volver al menú y usar Logout.

**Resultado esperado:** Login, inventario, carrito y entrada al checkout responden. Si alguno de estos pasos críticos falla, se detiene la prueba profunda de ese build.

## 4. Prueba de regresión

**Objetivo:** Verificar que un cambio en una parte de la tienda no rompió flujos que ya funcionaban. El escenario asume, por ejemplo, un ajuste en el ordenamiento del inventario o en el carrito.

**Pasos:**

1. Iniciar sesión con `standard_user` / `secret_sauce`.
2. Ordenar el inventario por Price (low to high) y luego por Price (high to low), y comprobar que la lista cambia de orden.
3. Agregar dos productos al carrito, abrir Your Cart y verificar que ambos están.
4. Completar el checkout con First Name, Last Name y Zip, y pulsar Finish.
5. Si se vuelve al inventario, usar Reset App State y Logout desde el menú.

**Resultado esperado:** El ordenamiento, el carrito, la confirmación "Thank you for your order!" y el cierre de sesión siguen funcionando después del cambio, aunque no fueran el objeto directo del arreglo.

## 5. Prueba de aceptación

**Objetivo:** Validar, desde la mirada del negocio o de un cliente, que la tienda permite completar una compra de punta a punta y que el resultado es comprensible. Es una UAT breve, no una cacería exhaustiva de defectos.

**Pasos:**

1. Entrar a SauceDemo como lo haría un comprador, con `standard_user` / `secret_sauce`.
2. Recorrer el inventario, elegir un producto y ver su detalle.
3. Agregarlo al carrito, revisar Your Cart e iniciar Checkout.
4. Completar First Name, Last Name y Zip, continuar y pulsar Finish.
5. Leer el mensaje final y decidir si el flujo sirve para dar por aceptada la compra.

**Resultado esperado:** El usuario de negocio puede terminar la compra sin ayuda y acepta el sistema si llega a "Thank you for your order!" y entiende que la orden quedó registrada. Si el flujo se entiende mal o se bloquea, la aceptación no se da, aunque otras pantallas no fallen.

---

## Error, defecto y falla

Ejemplo propio, observado en SauceDemo:

- Error: alguien cargó el producto con un nombre de prueba y no lo revisó.
- Defecto: el producto quedó guardado como `Test.allTheThings() T-Shirt (Red)`.
- Falla: en la tienda el usuario ve ese texto como título del producto, en lugar de un nombre claro.

**Contexto:** se observa con el usuario `standard_user`, tanto en la pantalla de inventario como en el detalle del producto. En la versión traducida del navegador el mismo título aparece como "Camiseta Test.allTheThings() (roja)". Para reportarlo conviene desactivar la traducción y copiar el texto original en inglés, porque el defecto está en los datos de la tienda, no en el traductor.
