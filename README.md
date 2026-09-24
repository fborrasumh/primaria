# PrimarIA

Generador de programaciones didácticas de **Educación Primaria** para la **Comunitat Valenciana**, en un único fichero HTML.

Hermana de [Genia](https://fborrasumh.github.io/genia/), que cubre ESO, Bachillerato, FP y EBPA. PrimarIA cubre la etapa de Primaria y sus particularidades: organización en tres ciclos, áreas en lugar de materias, criterios de evaluación y saberes básicos por ciclo, tutoría y globalización, y régimen lingüístico de lengua base.

## Qué hace

Recoge el contexto del centro, del grupo y de la forma de trabajar del maestro o la maestra, y redacta con 22 agentes especializados las 22 secciones de la programación: desde la portada y la justificación normativa hasta los anexos con rúbricas y registros. El documento se lee en pantalla, se copia en Markdown, se imprime en PDF o se descarga en Word.

## Marco normativo de referencia

- Ley Orgánica 3/2020 (LOMLOE)
- Real Decreto 157/2022, de ordenación y enseñanzas mínimas de Educación Primaria
- Decreto 106/2022 del Consell, de ordenación y currículo de Educación Primaria en la Comunitat Valenciana
- **Decreto 96/2026, de 19 de junio** (DOGV 10391, de 25.06.2026), que modifica el anterior y se aplica desde el curso 2026-2027
- Decreto 104/2018 y Orden 20/2019, de inclusión y respuesta educativa
- Ley 1/2024 de la Generalitat, de libertad educativa y elección de lengua base

### Qué incorpora del Decreto 96/2026

- Las áreas del artículo 9 en su nueva redacción; desaparece Proyectos Interdisciplinarios.
- El anexo IV completo: la app rellena las sesiones semanales con el horario oficial del área y el curso elegidos.
- El tiempo específico de lectura del segundo ciclo, con la estructura de sesión que fija el decreto, y la libre disposición del tercer ciclo ligada al plan de mejora.
- La evaluación en su nueva redacción: evaluación inicial, tres sesiones trimestrales, calificación por áreas en IN/SU/BI/NT/SB con observaciones cualitativas, e informes de final de ciclo y de etapa.
- El programa de lenguas vehiculares de la Ley 1/2024, en lugar de la terminología derogada de PEPLI, PLC y programas PEV, PIL o PIP.
- Los límites al uso de dispositivos digitales: 5 %, 15 % y 25 % del tiempo lectivo semanal por ciclo, sin sustituir al libro de texto.
- El aviso de que el anexo III ya incluye los criterios de evaluación del primer ciclo, que antes faltaban.

## Currículo oficial incrustado

La app lleva dentro el **anexo III consolidado**: el currículo del Decreto 106/2022 con la redacción que le da el Decreto 96/2026. Son 9 áreas con currículo, 65 competencias específicas, 633 criterios de evaluación repartidos entre los tres ciclos y 1.263 saberes básicos, en `<script id="kb-oficial">` dentro del propio `index.html`.

Cuando el área y el ciclo que se programan tienen currículo, los agentes reciben el texto literal —competencias específicas con su numeración y sus competencias clave, criterios con su código, saberes con su bloque, subbloque y grupo— y la orden de reproducirlo tal cual. Lo que aporta el modelo es la concreción al grupo, los indicadores de logro, los ejemplos, la secuenciación y las tablas. Se inyecta en las secciones 4, 5, 6, 7, 8, 9, 12, 13, 14 y 22.

Detalles que la app respeta porque el currículo se los dice:

- El decreto **no numera los descriptores operativos**. Las competencias clave se citan con su código a secas (CCL, CP, CMCT —STEM en Educación Física—, CD, CPSAA, CC, CE, CCEC) y el prompt prohíbe expresamente escribir CCL1 o STEM3.
- **Educación en Valores Cívicos y Éticos** solo tiene currículo en el tercer ciclo: si se elige un curso anterior, la app lo advierte en lugar de inventar criterios.
- **Religión** no tiene currículo en el decreto y se señala como tal.
- **Valenciano y Lengua Castellana comparten currículo**: el aviso llega al agente para que adapte la concreción a la lengua que se programa.
- **Música y Danza**: los criterios del Decreto 96/2026 cubren las competencias específicas 1 a 4; la 5 queda sin criterios asociados, y así se advierte.
- El horario semanal se rellena solo desde el anexo IV, y el ciclo se ajusta al curso elegido.

La pantalla «Currículo oficial» muestra la cobertura área por área y ciclo por ciclo, la procedencia del texto y las advertencias. Desde ahí puede cargarse otro JSON con el mismo esquema, que se guarda en `localStorage` y sustituye al incrustado.

Si hay que regenerarlo desde el PDF del DOGV, `extraer_anexo_iii.py` y el cuaderno `PrimarIA_curriculo.ipynb` hacen ese trabajo.

## Uso

Abre `index.html` en el navegador (o la versión publicada en GitHub Pages), introduce tu clave de API de OpenAI, rellena el formulario y genera. La clave se guarda solo en `localStorage` y viaja únicamente a la API de OpenAI. Las configuraciones se guardan como perfiles reutilizables y el texto generado persiste entre sesiones.

Modelo por defecto: `gpt-6-luna` (temperatura 1). Coste orientativo de una programación completa: unos céntimos.

## Aviso

El texto es un **borrador de trabajo**. Las competencias específicas, los criterios de evaluación y los saberes básicos deben contrastarse con el anexo del Decreto 106/2022 antes de entregar el documento. La responsabilidad de la programación es siempre del maestro o la maestra que la firma.

## Licencia

MIT. Fernando Borrás Rocher — Universidad Miguel Hernández de Elche.
