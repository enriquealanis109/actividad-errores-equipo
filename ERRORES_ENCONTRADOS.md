# Errores encontrados

**Nombre:**
**Fecha:**

> Tipos válidos: `Typo` (editor en rojo) · `Sintaxis` · `Terminal` (prisma / arranqu

e / endpoint / tests) · `Lógica`

| #   | Archivo                          | Línea | Tipo | ¿Qué estaba mal?                                                                             | ¿Cómo lo detectaste?                                           | ¿Cómo lo solucionaste?         |
| --- | -------------------------------- | ----- | ---- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------- | ------------------------------ |
| 0   | `src/ejemplo/ejemplo.service.ts` | 10    | Typo | _(fila de ejemplo, bórrala) se llamaba `this.prisma.usuaro` en vez de `this.prisma.usuario`_ | _VS Code lo marcó en rojo: "Property 'usuaro' does not exist"_ | _corregí el nombre del modelo_ |
| 1   | `prisma.config.ts`               | 10    | Typo    | En `datasource.url` estaba escrito `DATABASE_ULR` en vez de `DATABASE_URL`                             | VS Code lo marcó en rojo / error de referencia                                  | Corregí el nombre a `DATABASE_URL`                                                                          |
| 2   | `libro.controller.ts`            | 34    | Sintaxis| Faltaba convertir `id` de string a número (`id` en vez de `+id`)                                      | VS Code lo marcó con subrayado rojo por incompatibilidad de tipo                  | Agregué el signo `+` antes de `id` (`+id`)                                                                  |
| 3   | `prisma.service.ts`              | 6     | Typo    | Estaba mal escrito `PrismaClien` en vez de `PrismaClient`                                             | Revisando en `libro.service.ts` al pasar el cursor/inspeccionar sin aviso claro | Corregí la escritura de `PrismaClien` a `PrismaClient`                                                      |
| 4   | `libro.service.ts`               | 15    | Lógica  | En `create` se consultaba `libro.findUnique` en lugar de validar el autor (`autor.findUnique`)          | Lo detecté comparando/apoyándome con otro proyecto/ventana en VS Code             | Cambié la consulta en `create` de `libro.findUnique` a `autor.findUnique`                                   |
| 5   | `libro.service.ts`               | 22    | Lógica  | Referencia/campo incorrecto: se usaba `data.autorId` en vez de `data.categoriaId`                     | Lo detecté leyendo y revisando el código                                          | Cambié `data.autorId` por `data.categoriaId`                                                                |
| 6   | `libro.controller.ts`            | 29    | Lógica  | En `findAll` se pasaba `Number(categoriaId)` sin validar si venía vacío (`undefined` se volvía `NaN`) | Lo detecté leyendo el `findAll` y revisando cómo se recibía en el `GET`            | Cambié a `categoriaId ? Number(categoriaId) : undefined`                                                    |
| 7   | `libro.controller.ts`            | 36    | Lógica  | En `findOne` se convertía con `+id` como string sin validar el parámetro de ruta                       | Lo detecté leyendo la lógica del controlador                                      | Cambié a `return this.libroService.findOne(id)` y agregué `ParseIntPipe` para recibir `id: number`        |
| 8   |                                  |       |      |                                                                                              |                                                                |                                |
| 9   |                                  |       |      |                                                                                              |                                                                |                                |
| 10   |                                  |       |      |                                                                                              |                                                                |                                |
| 11   |                                  |       |      |                                                                                              |                                                                |                                |

<!-- Agrega todas las filas que necesites -->

## Reflexión final

1. ¿Qué tipo de error te costó más encontrar y por qué?
2. ¿Qué herramienta te ayudó más (editor, terminal, Swagger/Postman, tests)?
3. ¿Qué harías para evitar este tipo de errores en tus propios proyectos?
