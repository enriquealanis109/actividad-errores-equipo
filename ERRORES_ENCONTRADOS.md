# Errores encontrados

**Nombre: Roberto Trinidad **
**Fecha: 25/11/26**

> Tipos válidos: `Typo` (editor en rojo) · `Sintaxis` · `Terminal` (prisma / arranque / endpoint / tests) · `Lógica`

1| Archivo: prisma/prismaschema | Línea 63| Tipo typo | ¿Qué estaba mal? estaba escrito como ID en lugar de id| ¿Cómo lo detectaste?: dandole una lectura rapida del schema| ¿Cómo lo solucionaste? cambiando mayusculas por minusculas |

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

3| Archivo: src/prestamo/prestamo.service.ts | Línea: 33 | Tipo Lógica| ¿Qué estaba mal? estaba escrito < 0   | ¿Cómo lo detectaste? Probando los endpoints en thundercliente| ¿Cómo lo solucionaste? lo cambie por <= 0|

4| Archivo  src/prestamo/prestamo.service.ts | Línea 66| Tipo Sintaxis | ¿Qué estaba mal? no devolvia la fecha | ¿Cómo lo detectaste? endpoint | ¿Cómo lo solucionaste? solamente borre los parentesis y el NOT: |

5| Archivo src/prestamo/utils/fechas.ts | Línea: 10| Tipo Lógica | ¿Qué estaba mal? estaba en resta en lugar de suma | ¿Cómo lo detectaste? Lógica. leyendo un poco, y repasando que estaba mal | ¿Cómo lo solucionaste? le cambie el - por el +  |

6| Archivo src/prestamo/prestamo.service.ts | Línea: 81 | Tipo:Sintaxis | ¿Qué estaba mal? no buscaba las fechas correctamente| ¿Cómo lo detectaste? me salia error en las pruebas | ¿Cómo lo solucionaste? me sujeria cambiarlo gt por lt: segun gt es mayor que y lt es menor que asi que eso cambie |

7| Archivo src/prestamo/utils/fechas.ts | Línea: 23| Tipo: Tipos válidos: `Typo` | ¿Qué estaba mal? estaba !== | ¿Cómo lo detectaste? lei como tres veces fecha.ts| ¿Cómo lo solucionaste? solo le cambio el ! por = |

8| Archivo src/prestamo/prestamo.controller.ts| Línea27 | Tipo Terminal| ¿Qué estaba mal? no veia un id valido | ¿Cómo lo detectaste? la terminal aparecia error en la linea 27 del archivo| ¿Cómo lo solucionaste? cambie el `vencido` por `:id` |

9| Archivo src/prisma/prisma.service.ts | Línea 6| Tipo(editor en rojo)  | ¿Qué estaba mal? faltaba la t en el export| ¿Cómo lo detectaste? no podia arrancar el prisma| ¿Cómo lo solucionaste? le agg la t |

10| Archivo main  | Línea 9| Tipo Terminal` (prisma / arranque / endpoint / tests) | ¿Qué estaba mal? el app user no cerraba en parentesis | ¿Cómo lo detectaste? al probar arrancar | ¿Cómo lo solucionaste? lo cerre correctamente |

## Reflexión final

1. ¿Qué tipo de error te costó más encontrar y por qué?
2. ¿Qué herramienta te ayudó más (editor, terminal, Swagger/Postman, tests)?
3. ¿Qué harías para evitar este tipo de errores en tus propios proyectos?
