# Errores encontrados

**Nombre: Roberto Trinidad **
**Fecha: 25/11/26**

> Tipos válidos: `Typo` (editor en rojo) · `Sintaxis` · `Terminal` (prisma / arranque / endpoint / tests) · `Lógica`

1| Archivo: prisma/prismaschema | Línea 63| Tipo typo | ¿Qué estaba mal? estaba escrito como ID en lugar de id| ¿Cómo lo detectaste?: dandole una lectura rapida del schema| ¿Cómo lo solucionaste? cambiando mayusculas por minusculas |

2| Archivo  src/prestamo/prestamo.service.ts| Línea 27 | Tipo: Sintaxis | ¿Qué estaba mal?: faltaba colocar un await | ¿Cómo lo detectaste? me aparecio el error cuando abri el archivo | ¿Cómo lo solucionaste? escribiendo await donde correspondia |

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
me costo encontrar mas los errores que no te avisa la terminal.

3. ¿Qué herramienta te ayudó más (editor, terminal, Swagger/Postman, tests)?
la terminal me ayudo mas ya que me aparece algunas recomendaciones y las cosas que estan mal, el motivo con el cual no funciona
  
5. ¿Qué harías para evitar este tipo de errores en tus propios proyectos?
leer mejor las documentaciones y leer mas veces mi propio codigo
   
