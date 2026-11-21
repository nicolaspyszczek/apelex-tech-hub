# Apelex Tech Hub 2.3.0 — análisis para portfolio

## Fuente y alcance

Análisis estático de `Apelex_Tech_Hub_2.3.0.apk` (APK de 48 MB), descomprimido e inspeccionado en sus recursos web, JavaScript, base SQLite, imágenes y clases Android. La inspección confirma contenido y lógica empaquetados, pero no equivale a una prueba funcional en un dispositivo ni a una auditoría del backend Firebase en producción.

## Descripción del producto

Apelex Tech Hub es una aplicación educativa híbrida para Android, construida alrededor de una experiencia web local. Su propósito es enseñar soporte IT y competencias digitales mediante cursos progresivos, lecciones guiadas, ejercicios, simuladores y una capa de gamificación opcional.

La aplicación ofrece dos experiencias:
- **Modo estándar:** recorrido de aprendizaje centrado en cursos y prácticas.
- **Modo lúdico:** incorpora historia, campeones, distritos, XP, ligas, pase de batalla, equipamiento y combates.

## Contenido académico verificado

- 15 cursos: 5 de Principiante, 5 de Intermedio y 5 de Aplicación avanzada.
- 45 lecciones guiadas, 3 por curso.
- Cada lección incluye 8 bloques didácticos: introducción, propósito, funcionamiento, glosario/relaciones, caso de trabajo, procedimiento, errores y comprobaciones, y resumen/preparación.
- 3 preguntas de práctica por lección: 135 preguntas.
- Cada curso tiene una evaluación de 4 preguntas: 60 preguntas de evaluación en total. Se aprueba con 3 de 4 (75 %), una vez completadas las nueve preguntas de sus tres lecciones.
- Cada curso incluye un proyecto práctico con borrador, lista de revisión y confirmación personal.
- La aplicación genera constancias personales imprimibles/guardables como PDF. El texto de la propia app aclara que no son certificaciones institucionales ni acreditan experiencia laboral.

### Cursos

**Principiante**
1. PC y Windows desde cero
2. Redes e internet para soporte
3. Mesa de ayuda y comunicación
4. Excel, datos y CRM inicial
5. Seguridad, web e inglés técnico inicial

**Intermedio**
6. Soporte corporativo de usuarios
7. Redes y acceso a servicios
8. Soporte SaaS, APIs y QA
9. SQL y análisis operativo
10. CRM, ventas tech y Customer Success

**Aplicación avanzada**
11. Automatizaciones e integraciones confiables
12. JavaScript para tareas operativas
13. Linux, nube y observabilidad
14. Operaciones IT y mejora del servicio
15. IA aplicada, portafolio e inserción laboral

## Laboratorios y herramientas

La app incluye cinco laboratorios principales:
1. **Terminal y redes:** simulador educativo de comandos `ipconfig`, `ping`, `tracert` y `nslookup`. Las salidas son simuladas; no ejecuta comandos en el dispositivo ni hace pruebas reales de red.
2. **Helpdesk:** tres tickets ficticios, priorización P1–P4 y selección del siguiente paso técnico.
3. **CRM y ventas B2B:** conversación simulada con prospecto y calificación BANT (Need, Budget, Authority, Timeline). No se conecta a un CRM real.
4. **Automatización e IA:** diseñador de flujo simulado Gmail → Jira con validación de etiqueta, mapeo de campos, deduplicación y reintentos limitados. El resultado es una simulación; no envía correos ni crea tickets reales. Incluye un evaluador heurístico de prompts, no un modelo generativo.
5. **Quiz:** ocho preguntas de repaso con explicaciones.

Además hay repaso de errores, plan de aprendizaje, enlaces a documentación externa, exportación de progreso y descarga del portfolio de prácticas en Markdown.

## OCR verificado

- Escáner «Foto al error» para seleccionar una imagen/captura.
- OCR local con Tesseract.js 7.
- Idiomas configurados: inglés y español (`eng+spa`).
- El código indica un máximo de 12 MB por imagen y procesamiento en el dispositivo, sin enviar la imagen a un servidor.

## Gamificación y arte

- 5 campeones: Kato (Hardware), Ryn (Sistemas Linux), Elara (Código Python y APIs), Liam (Redes) y Nala (Helpdesk).
- 5 ligas: Hierro, Bronce, Plata, Oro y Grandmaster; 10 niveles por liga.
- 50 niveles por campeón: 250 registros de pase de batalla en total (confirmados en cinco tablas SQLite, 50 filas cada una).
- Recompensas y equipamiento desbloqueable: armas, guantes, botas, cascos, armaduras, capas, escudos, accesorios, auras, emotes, aspectos y tronos.
- Ventajas diferenciadas por campeón (resistencia, infiltración, poder, alcance y equipo).
- Avatares con dos presentaciones: ilustración anime 2D y modelos 3D construidos con Three.js; el visor permite girarlos y equiparlos.
- Combates de preguntas contra avatares corrompidos: las respuestas correctas permiten atacar; los errores o el tiempo agotado habilitan el ataque rival. Hay opciones de 18 o 30 segundos por pregunta.
- Desafío narrativo de Boss Bug Error 500.
- Siete formatos de minijuegos de estudio identificados en el código: sopa de letras, crucigrama, acertijo, unir conceptos, ordenar pasos, completar y encontrar el error.

## Arquitectura técnica observada

- APK Android con una aplicación web empaquetada en un WebView y puente nativo Android.
- Interfaz principal tipo SPA en HTML/CSS/JavaScript; el bundle de componentes auxiliares usa React.
- Three.js para los modelos 3D de personajes y combate.
- Tesseract.js 7 + modelos de idioma español/inglés para OCR local.
- Persistencia local mediante almacenamiento nativo/localStorage; IndexedDB para datos de referencia.
- SQLite local con cinco tablas de pase de batalla (TOP, JUNGLE, MID, ADC y SUPPORT), 50 niveles por tabla.
- Flujo de cuenta con Google, correo/contraseña, recuperación de contraseña y entrada como invitado.
- Código de sincronización con Firebase Authentication y Firestore mediante un puente nativo Android. El modo invitado guarda el progreso en el dispositivo. El controlador contempla fusión de progreso, registro de cambios por campo y resolución de conflictos.
- La inspección estática confirma el código de integración, pero no verifica que el proyecto Firebase, sus reglas ni el inicio de sesión/sincronización estén operativos actualmente.
- La app puede usarse como invitado sin autenticar. La demo web aislada del portfolio no tendrá el puente nativo Android. En este paquete se ocultaron las opciones Google/correo y se dejaron visibles los accesos de invitado; también se vaciaron los valores de configuración pública Firebase de la copia web. El progreso queda local en el navegador y no se sincroniza con Firestore.
- No se encontró un service worker; no describirla como PWA instalable. La instalación Android corresponde al APK híbrido.

## Límites y afirmaciones que NO conviene hacer

- No afirmar que el Oráculo IA es un chatbot conectado a un LLM: en esta APK es un personaje narrativo. No se encontraron llamadas a OpenAI, Gemini, Anthropic ni endpoints de modelos generativos.
- No afirmar que los laboratorios de CRM, Gmail, Jira o terminal operan servicios reales: son simulaciones didácticas.
- No afirmar que las constancias tienen aval académico, acreditación externa o equivalencia con una certificación profesional.
- No afirmar que el OCR se envía a la nube: el código describe procesamiento local.
- No afirmar que se verificó en vivo Firebase, login Google, sincronización, reglas de seguridad ni rendimiento en distintos dispositivos.
- No afirmar que se probó visualmente en navegador desde esta inspección estática.

## Diferencia de identidad a resolver

En la configuración narrativa empaquetada, la ciudad figura literalmente como **Apple City** y el campo de ubicación está vacío. El contenido inspeccionado no menciona Resistencia ni Chaco. Si el concepto vigente del producto es Apelex City, Resistencia, Chaco, conviene decidir si esta APK representa una versión anterior y corregir la identidad narrativa en el portfolio/demo, sin atribuir esa localización a la versión 2.3.0 inspeccionada.

## Recomendación para el portfolio

Crear un caso independiente de Chambot, con:
- Ruta de caso `#/casos/apelex`.
- Ruta de demo `#/demo/apelex`.
- Caso de estudio centrado en el problema, propuesta, arquitectura, experiencia de aprendizaje, gamificación, OCR local y persistencia.
- Demo web aislada basada en el build web extraído, abierta como invitado. No mezclar sus estilos ni su estado con el portfolio ni con la demo de Chambot.
- Mantener los assets originales y optimizar la carga. El paquete OCR ocupa aproximadamente 61.7 MiB sin comprimir; si se decide excluirlo para reducir peso, ocultar la herramienta OCR en la demo y aclarar que esa función pertenece a la APK completa.
- No alterar las secciones, estilos ni rutas existentes de Chambot.

## Datos de participación

La APK permite describir el producto y su implementación, pero no determina por sí sola qué tareas realizó personalmente el titular del portfolio. El texto final debe reflejar el rol real del usuario y no atribuirle en automático toda la autoría del código, los modelos gráficos o los contenidos.
