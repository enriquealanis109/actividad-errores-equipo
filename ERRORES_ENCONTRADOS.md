# Errores encontrados

**Fecha:** 25/11/2026

> Tipos válidos: `Typo` (editor en rojo) · `Sintaxis` · `Terminal` (prisma / arranque / endpoint / tests) · `Lógica`

---

## Enrique Alanis — Autores, Categorías y main.ts

| #   | Archivo                               | Línea | Tipo     | ¿Qué estaba mal?                                               | ¿Cómo lo detectaste?                                   | ¿Cómo lo solucionaste?                             |
| --- | ------------------------------------- | ----- | -------- | -------------------------------------------------------------- | ------------------------------------------------------ | -------------------------------------------------- |
| 1   | `prisma/schema.prisma` (modelo Autor) | —     | Terminal | El campo `nombre` decía `Strng` en vez de `String`             | `npx prisma generate` falló / VS Code en rojo          | Cambié `Strng` por `String`                        |
| 2   | `src/autor/autor.controller.ts`       | 24    | Typo     | `@Gett()` en vez de `@Get()`                                   | VS Code en rojo                                        | Corregí a `@Get()`                                 |
| 3   | `src/autor/dto/create-autor.dto.ts`   | 11    | Typo     | `@IsOptinal()` en vez de `@IsOptional()`                       | VS Code en rojo                                        | Corregí a `@IsOptional()`                          |
| 4   | `src/categoria/categoria.service.ts`  | 26    | Sintaxis | Faltaba la coma después de `orderBy: { nombre: 'asc' }`        | VS Code en rojo / no compilaba                         | Agregué la coma                                    |
| 5   | `src/autor/autor.service.ts`          | 23    | Lógica   | `if (autor)` invertido: lanzaba 404 cuando el autor SÍ existía | Probando `GET /autores/:id` con un id real daba 404    | Cambié a `if (!autor)`                             |
| 6   | `src/categoria/categoria.module.ts`   | 6     | Terminal | `providers: []` vacío, faltaba `CategoriaService`              | Nest truena al arrancar ("can't resolve dependencies") | Importé y agregué `CategoriaService` a `providers` |
| 7   | `src/main.ts`                         | 9     | Sintaxis | El `ValidationPipe` estaba suelto, fuera de `useGlobalPipes()` | No compilaba / Nest no arrancaba                       | Lo metí dentro de `useGlobalPipes(...)`            |

---

## Kevin — Libros y configuración

| #   | Archivo                         | Línea | Tipo     | ¿Qué estaba mal?                                                                          | ¿Cómo lo detectaste?                  | ¿Cómo lo solucionaste?                                   |
| --- | ------------------------------- | ----- | -------- | ----------------------------------------------------------------------------------------- | ------------------------------------- | -------------------------------------------------------- |
| 1   | `prisma.config.ts`              | 10    | Typo     | `DATABASE_ULR` en vez de `DATABASE_URL`                                                   | VS Code en rojo / error de referencia | Corregí a `DATABASE_URL`                                 |
| 2   | `src/prisma/prisma.service.ts`  | 6     | Typo     | `PrismaClien` en vez de `PrismaClient` (faltaba la `t`)                                   | No arrancaba Prisma                   | Corregí a `PrismaClient`                                 |
| 3   | `src/libro/libro.controller.ts` | 34    | Sintaxis | Faltaba convertir `id` a número (`id` en vez de `+id`)                                    | VS Code en rojo por tipo              | Agregué `+id`                                            |
| 4   | `src/libro/libro.service.ts`    | 15    | Lógica   | En `create` consultaba `libro.findUnique` en vez de validar el autor (`autor.findUnique`) | Comparando con otro código            | Cambié a `autor.findUnique`                              |
| 5   | `src/libro/libro.service.ts`    | 22    | Lógica   | Usaba `data.autorId` en vez de `data.categoriaId`                                         | Leyendo el código                     | Cambié a `data.categoriaId`                              |
| 6   | `src/libro/libro.controller.ts` | 29    | Lógica   | `findAll` hacía `Number(categoriaId)` sin validar vacío (`NaN`)                           | Leyendo el `findAll`                  | Cambié a `categoriaId ? Number(categoriaId) : undefined` |
| 7   | `src/libro/libro.controller.ts` | 36    | Lógica   | `findOne` convertía con `+id` sin validar                                                 | Leyendo el controlador                | Cambié a `findOne(id)` + `ParseIntPipe`                  |

---

## Roberto Trinidad — Préstamos

| #   | Archivo                               | Línea | Tipo     | ¿Qué estaba mal?                            | ¿Cómo lo detectaste?                 | ¿Cómo lo solucionaste?             |
| --- | ------------------------------------- | ----- | -------- | ------------------------------------------- | ------------------------------------ | ---------------------------------- |
| 1   | `prisma/schema.prisma`                | 63    | Typo     | Estaba escrito `ID` en vez de `id`          | Lectura rápida del schema            | Cambié mayúsculas por minúsculas   |
| 2   | `src/prestamo/prestamo.service.ts`    | 27    | Sintaxis | Faltaba un `await`                          | Error al abrir el archivo            | Agregué `await` donde correspondía |
| 3   | `src/prestamo/prestamo.service.ts`    | 33    | Lógica   | Estaba `< 0`                                | Probando endpoints en Thunder Client | Cambié a `<= 0`                    |
| 4   | `src/prestamo/prestamo.service.ts`    | 66    | Sintaxis | No devolvía la fecha                        | Endpoint                             | Borré los paréntesis y el `NOT`    |
| 5   | `src/prestamo/prestamo.service.ts`    | 81    | Lógica   | `gt` en vez de `lt` (mayor que / menor que) | Error en las pruebas                 | Cambié `gt` por `lt`               |
| 6   | `src/prestamo/utils/fechas.ts`        | 10    | Lógica   | Era una resta en vez de una suma            | Leyendo y repasando                  | Cambié `-` por `+`                 |
| 7   | `src/prestamo/prestamo.controller.ts` | 27    | Terminal | No recibía un `id` válido                   | Error en la terminal (línea 27)      | Cambié `vencido` por `:id`         |

---

## Iván Jiménez— Socios y configuración de Prisma**

| #   | Archivo                                  | Línea | Tipo     | ¿Qué estaba mal?                                                             | ¿Cómo lo detectaste?                                  | ¿Cómo lo solucionaste?                                                    |
| --- | ---------------------------------------- | ----- | -------- | ---------------------------------------------------------------------------- | ----------------------------------------------------- | ------------------------------------------------------------------------- |
| 1   | `src/socio/socio.module.ts`              | 3     | Typo     | La importación de `SocioService` no tenía la extensión `.js`                 | VS Code en rojo                                       | Agregué la extensión `.js`                                                |
| 2   | `prisma/schema.prisma` (modelo Autor)    | 12    | Terminal | El campo `nombre` decía `Strng` en vez de `String`                           | `npx prisma generate` falló / VS Code en rojo         | Cambié `Strng` por `String`                                               |
| 3   | `prisma/schema.prisma` (modelo Prestamo) | 63    | Terminal | La referencia decía `ID` en vez de `id`                                      | `npx prisma generate` falló con error P1012           | Cambié `references: [ID]` por `references: [id]`                          |
| 4   | `src/prisma/prisma.service.ts`           | 6     | Typo     | `PrismaClien` en vez de `PrismaClient`                                       | VS Code en rojo                                       | Corregí el nombre a `PrismaClient`                                        |
| 5   | `src/socio/dto/create-socio.dto.ts`      | 2     | Typo     | `IsEmail` se importaba desde `class-transformer` en vez de `class-validator` | VS Code en rojo / error de importación                | Cambié la importación a `class-validator`                                 |
| 6   | `prisma.config.ts`                       | 10    | Terminal | La variable decía `DATABASE_ULR` en vez de `DATABASE_URL`                    | `npx prisma migrate dev --name init` falló            | Corregí `DATABASE_ULR` por `DATABASE_URL`                                 |
| 7   | `src/socio/socio.controller.ts`          | 27    | Sintaxis | Faltaba una llave `}` para cerrar el método `findAll()`                      | `npm run build` mostró errores de sintaxis en cascada | Agregué la llave de cierre y corregí la ubicación de la llave de la clase |

---


   
=======
## Reflexiones

### Enrique Alanis — Autores, Categorías y main.ts

1. **¿Qué tipo costó más?** El de **Lógica** (el `if (autor)` invertido en `findOne`), porque no salía en rojo — solo lo detecté probando `GET /autores/:id` con un id que existía y me daba 404 en vez del autor.
2. **¿Qué herramienta ayudó más?** Swagger para cazar el de lógica probando el endpoint.
3. **¿Cómo evitarlos?** Probar cada endpoint contra las reglas del README, hacer commits pequeños y revisar bien antes de subir.

### Kevin — Libros y configuración

1. **¿Qué tipo costó más?**
2. **¿Qué herramienta ayudó más?**
3. **¿Cómo evitarlos?**

### Roberto Trinidad — Préstamos


1. ¿Qué tipo de error te costó más encontrar y por qué?
me costo encontrar mas los errores que no te avisa la terminal.

3. ¿Qué herramienta te ayudó más (editor, terminal, Swagger/Postman, tests)?
la terminal me ayudo mas ya que me aparece algunas recomendaciones y las cosas que estan mal, el motivo con el cual no funciona
  
5. ¿Qué harías para evitar este tipo de errores en tus propios proyectos?
leer mejor las documentaciones y leer mas veces mi propio codigo

### Ivan jimenez — Préstamos

1. **¿Qué tipo costó más? El que más me costó fue el error de sintaxis por la llave que faltaba en el controlador de Socios. Me tomó bastante tiempo encontrar dónde estaba el problema y entender por qué estaba generando tantos errores. Fue el último que logré solucionar.**
2. **¿Qué herramienta ayudó más? VS Code fue una de las herramientas que más me ayudó, porque me señalaba los errores directamente en el código. También utilicé la terminal para ejecutar los comandos y comprobar si los cambios estaban funcionando.**
3. **¿Cómo evitarlos? Revisando con más cuidado el código a medida que se va escribiendo, respetando la estructura de cada archivo y comprobando los cambios poco a poco. También es importante no dejar pasar los errores que aparecen, porque uno pequeño puede terminar causando muchos más.**
