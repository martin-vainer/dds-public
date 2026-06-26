# Metodología de apuntes DDS

Este documento define cómo convertir material disperso de DDS —PDFs, tomas propias, repos de código y transcripciones— en apuntes útiles para estudiar, rendir y generar material derivado con agentes.

## Objetivo pedagógico

El apunte no busca transcribir la clase palabra por palabra.

Busca reconstruir la clase para que sirva para:

- entender conceptos;
- conectar teoría con código real;
- repasar antes del examen;
- detectar errores típicos;
- generar cuestionarios, flashcards, mapas conceptuales y simulacros de oral.

Regla central:

> Conceptos > transcripción. El apunte tiene que explicar por qué existe cada cosa, qué problema resuelve y cómo se ve en código.

## Principios

1. **Orden de comprensión > orden del PDF**  
   Si un tema necesita otro para entenderse, va después aunque el PDF lo muestre antes.

2. **Teoría conectada con práctica**  
   Siempre que haya repo de clase, el concepto debe aterrizar en un archivo, flujo o fragmento real.

3. **Fuente explícita**  
   Cada clase debe declarar PDFs, tomas propias, caches de texto y ramas/repos usados.

4. **Gotchas visibles**  
   Si el README dice una cosa y el código hace otra, se registra. No se tapa.

5. **Cierre orientado a examen**  
   Cada clase debe terminar con resumen mental y checklist.

6. **Plantilla flexible**  
   No todos los conceptos necesitan todos los subtítulos. Los conceptos centrales sí; los secundarios pueden ser más breves.

## Jerarquía de fuentes

Al generar o revisar apuntes, usar esta prioridad:

1. PDF/material oficial de cátedra.
2. Transcripción/cache en `_cache_pdf_text/`.
3. Toma propia de apuntes en Markdown.
4. Repositorio de código de la clase.
5. README/documentación del repo de código.
6. Links recomendados por cátedra.
7. Conocimiento externo, solo como apoyo y señalándolo.

### Uso de `_cache_pdf_text/`

La carpeta `_cache_pdf_text/` es una fuente de alto valor para agentes.

- Los PDFs son la autoridad visual/original.
- Los `.txt`/`.md` cacheados son la versión rápida para búsqueda, extracción y contraste.
- Antes de leer un PDF binario, revisar si existe su cache textual.
- Si falta cache para una clase nueva, **generarlo antes de escribir el apunte**.
- Si no se puede generar por un problema técnico, recién ahí registrar la ausencia como pendiente y avisar.
- Si el cache y el PDF parecen diferir, priorizar el PDF y regenerar el cache.

Regla práctica:

```txt
PDF oficial -> autoridad
_cache_pdf_text -> lectura rápida para agentes
apunte final -> síntesis pedagógica
```

### Workflow obligatorio para una clase nueva

Antes de generar apuntes de una clase con PDFs:

1. Identificar los PDFs de la clase en `Clases_Practica/` y/o `Clases_Teoria/`.
2. Buscar su transcripción correspondiente en `_cache_pdf_text/`.
3. Si no existe, generarla en `_cache_pdf_text/` con nombre estable y legible.
4. Usar esa transcripción para búsqueda, extracción y contraste.
5. Usar el PDF original como respaldo/autoridad si hay dudas de formato, diagramas o contenido visual.
6. Registrar en `docs/indice-clases.md` el path del cache textual generado.

Regla:

> No empezar a redactar el apunte final de una clase nueva si sus PDFs principales todavía no tienen cache textual, salvo que el usuario pida explícitamente saltearlo.

## Estructura estándar de una clase

```md
## Clase XX - Tema

Fuente teórica:
- PDF local: ...
- Cache textual: ...

Fuente práctica / código:
- Repo/rama: ...
- Carpeta local: ...

Toma propia:
- ...

Links recomendados:
- ...

Idea central:
> ...

Por qué importa:
...

---

### 1) Primer concepto base
...

### 2) Segundo concepto
...

### N) Gotchas reales del repo
...

### N+1) Resumen mental de Clase XX
...

Checklist para examen:
- ...
```

No forzar todos los bloques si una clase no tiene repo o no tiene links recomendados.

## Estructura estándar de un concepto

Para conceptos importantes:

```md
### N) Concepto

#### Problema
Qué problema intenta resolver.

#### Concepto
Definición clara y breve.

#### Modelo mental
Flujo, analogía o diagrama si ayuda.

#### Ejemplo mínimo
Ejemplo pequeño y aislado.

#### Ejemplo real del repo
Archivo/rama/fragmento donde aparece.

#### Error típico
Confusión frecuente o mala práctica.

#### Para examen
Respuesta corta que podría decirse oralmente.
```

Para conceptos secundarios, alcanza con:

```md
### N) Concepto

Definición + ejemplo + relación con la clase.
```

## Criterios para ordenar temas

Ordenar por dependencia conceptual, no por aparición cronológica.

Ejemplo frontend:

```txt
crear/arrancar app
  -> montaje en el DOM
  -> componentes y JSX
  -> props
  -> state
  -> listas/eventos
  -> routing
  -> integración/API
```

Ejemplo backend:

```txt
HTTP
  -> rutas
  -> controller
  -> service
  -> repository
  -> dominio
  -> errores
  -> tests
  -> documentación
```

## Cómo usar ejemplos del repo

No pegar código sin explicación.

Patrón recomendado:

```md
Ejemplo real del repo:

```js
// fragmento relevante
```

Fuente:
- link o path

Lectura:
```txt
request -> controller -> service -> repository
```

Qué muestra:
- responsabilidad de cada pieza;
- por qué está ubicado ahí;
- qué error evita.
```

## Gotchas

Los gotchas deben ser concretos y verificables.

Ejemplos:

```md
1. README dice búsqueda en tiempo real, pero el código filtra al presionar Buscar.
2. La función async existe, pero todavía no se usa en componentes.
3. Esto sirve para la clase, pero en producción convendría validar X.
```

## Resumen mental y checklist

Cada clase debe cerrar con:

```md
Si te preguntan "qué aporta esta clase?", contestá:

> Respuesta oral compacta.

Checklist para examen:
- concepto clave 1;
- concepto clave 2;
- error típico;
- ejemplo real.
```

El resumen mental es obligatorio porque transforma el apunte en discurso de examen.

## Convención de nombres a futuro

No hace falta renombrar masivamente material histórico. Desde ahora, para nuevos archivos generados por agentes, preferir nombres estables, sin espacios y en minúscula:

```txt
clase-11-practica-integracion-front-back.md
clase-11-practica-integracion-front-back.pdf
clase-11-practica-integracion-front-back.cache.md
clase-13-teoria-despliegue.md
```

Reglas:

- usar `clase-XX` con dos dígitos;
- indicar `practica` o `teoria`;
- incluir tema corto;
- evitar tildes, espacios y signos raros en archivos nuevos generados;
- no renombrar PDFs oficiales históricos salvo decisión explícita.

## Derivados de estudio

Los apuntes finales pueden alimentar:

```txt
study/preguntas/
study/flashcards/
study/mapas-conceptuales/
study/glosario.md
```

Regla:

> El apunte principal explica. `study/` entrena.

No mezclar cuestionarios o flashcards dentro del apunte principal salvo que sea una sección explícita de repaso.
