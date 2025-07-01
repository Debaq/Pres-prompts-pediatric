# Guía Práctica: Ingeniería de Prompts para Pediatría

**Sociedad Peruana de Pediatría - Curso de Inteligencia Artificial 2025**  
**Ms. Nicolás Baier - Tecnólogo Médico**  
**TECMEDHUB - Universidad Austral de Chile**

---

## ⚠️ Advertencia Importante

**Esta información corresponde a julio de 2025 y puede cambiar rápidamente.** Los modelos de IA, sus características, precios y capacidades evolucionan constantemente. Se recomienda verificar la información actualizada antes de tomar decisiones.

**🚨 RECORDATORIO CRÍTICO PARA USO CLÍNICO:** Los LLMs pueden inventar información médica que suena convincente pero es falsa. NUNCA usar IA para diagnósticos definitivos. Siempre verificar datos, referencias bibliográficas y recomendaciones terapéuticas antes de aplicar en práctica clínica.

---

## Fundamentos Técnicos en Medicina

### ¿Por qué funcionan los prompts en contexto médico?

Para maximizar el potencial de la IA en pediatría, es fundamental comprender los principios técnicos que permiten a los modelos de lenguaje grandes (LLMs) generar respuestas clínicamente útiles y estructuradas.

**Arquitectura Transformer aplicada a medicina**

Los modelos como ChatGPT, Claude y Gemini utilizan arquitectura Transformer con mecanismos de atención que pueden "enfocarse" en síntomas relevantes, signos clínicos críticos, y patrones diagnósticos. Cuando proporcionamos un prompt médico detallado con información clínica específica (edad, peso, síntomas, antecedentes), el mecanismo de atención prioriza esta información médica por sobre datos irrelevantes.

El contexto posicional es crucial en medicina: los síntomas principales mencionados al inicio del prompt reciben mayor peso que información secundaria. Esto significa que estructurar correctamente la presentación del caso (motivo de consulta → antecedentes → examen físico → estudios) mejora significativamente la calidad de la respuesta.

**Entrenamiento médico masivo**

Los LLMs han procesado millones de textos médicos: papers de PubMed, libros de pediatría, guías clínicas, casos clínicos, y protocolos hospitalarios. Durante este entrenamiento, absorben patrones implícitos de razonamiento clínico específicos de cada especialidad médica.

Cuando usamos role-playing médico ("actúa como neonatólogo"), activamos estos patrones especializados. El modelo ha visto miles de ejemplos de cómo escriben los neonatólogos, qué terminología usan, cómo estructuran diagnósticos diferenciales, y qué nivel de detalle proporcionan para diferentes grupos etarios.

**Capacidades emergentes en razonamiento clínico**

Una característica notable es la emergencia de razonamiento clínico que no fue explícitamente programado. Los modelos pueden aplicar principios diagnósticos aprendidos en un contexto a situaciones clínicas nuevas. Por ejemplo, si aprendieron sobre razonamiento diferencial en cardiología, pueden aplicar lógica similar a neumología pediátrica.

Esta transferencia explica por qué el zero-shot prompting funciona en medicina: cuando presentamos un caso pediátrico que el modelo nunca vio exactamente, puede generalizar desde patrones similares en su entrenamiento médico para generar diagnósticos diferenciales coherentes.

**In-context learning médico**

Los modelos pueden "aprender" nuevos patrones clínicos dentro del mismo prompt observando ejemplos médicos, sin modificar sus parámetros internos. Cuando proporcionamos casos clínicos similares como ejemplos (few-shot), el modelo identifica el patrón diagnóstico subyacente y lo aplica al nuevo caso.

Esta capacidad es especialmente útil para protocolos hospitalarios específicos o guidelines locales que pueden diferir de la literatura general incluida en el entrenamiento.

**Chain-of-thought en razonamiento clínico**

La investigación demuestra que cuando pedimos a los modelos mostrar razonamiento diagnóstico paso a paso, su precisión mejora significativamente en problemas médicos complejos. Esto ocurre porque la descomposición de casos complejos en pasos diagnósticos secuenciales (anamnesis → examen físico → diagnósticos diferenciales → estudios confirmatorios) permite procesamiento más preciso de cada componente.

Desde perspectiva técnica, el Chain-of-Thought reduce la carga cognitiva en cada paso de generación, permitiendo al modelo construir razonamiento clínico incrementalmente, usando cada conclusión previa como contexto para el siguiente paso diagnóstico.

---

## Tipos de Prompting en Pediatría

### 1. Prompting Básico Médico
**Funciona porque:** Utiliza conocimiento médico pre-entrenado directo  
**Usar para:** Dosificaciones estándar, definiciones médicas, clasificaciones pediátricas

**Ejemplo:**
```
Define bronquiolitis según criterios actuales de la Academia Americana de Pediatría.
```

### 2. Zero-Shot Prompting Clínico  
**Funciona porque:** **Transferencia de conocimiento médico** - generaliza desde casos similares  
**Usar para:** Diagnósticos diferenciales, protocolos de manejo, análisis de síntomas nuevos

**Ejemplo:**
```
Lactante de 8 meses con fiebre, tos y dificultad respiratoria. 
Genera diagnóstico diferencial estructurado por probabilidad.
```

### 3. Few-Shot Prompting con Casos Clínicos
**Funciona porque:** **In-context learning médico** - aprende patrones diagnósticos de ejemplos  
**Usar para:** Análisis de casos complejos, aplicación de protocolos específicos

**Ejemplo:**
```
Clasifica urgencia pediátrica:

Caso 1: "Lactante 3 meses, fiebre 39°C, irritable" → URGENCIA ALTA
Caso 2: "Niño 5 años, tos seca 2 días, afebril" → URGENCIA BAJA  

Clasifica: "RN 15 días, ictericia hasta abdomen"
```

### 4. Chain-of-Thought Diagnóstico
**Funciona porque:** **Descomposición de razonamiento clínico** - reduce errores diagnósticos  
**Respaldo científico:** Wei et al. (2022) - mejora significativa en razonamiento médico  
**Usar para:** Casos complejos, diagnósticos diferenciales extensos, decisiones terapéuticas

**Ejemplo:**
```
Analiza este caso paso a paso:
Paso 1: Sistematiza signos y síntomas
Paso 2: Genera diagnósticos diferenciales  
Paso 3: Prioriza estudios complementarios
Paso 4: Establece plan de manejo
```

### 5. Role-Playing Médico Especializado
**Funciona porque:** **Priming de expertise** - activa conocimiento subspecializado  
**Usar para:** Consultas especializadas, segundas opiniones, casos multidisciplinarios

**Ejemplo:**
```
Actúa como neonatólogo con 15 años de experiencia en UCIN. 
Evalúa este RN prematuro con distress respiratorio...
```

### 6. Meta-Prompting Médico
**Funciona porque:** **Auto-optimización contextual** - la IA diseña prompts médicos óptimos  
**Usar para:** Cuando sabes QUÉ necesitas clínicamente pero no CÓMO pedirlo efectivamente

**Ejemplo:**
```
Necesito analizar 10 estudios sobre asma en preescolares para actualizar 
nuestro protocolo. Crea un prompt que extraiga: metodología, poblaciones, 
intervenciones, outcomes y aplicabilidad clínica.
```

---

## Template Universal para Consultas Pediátricas

```
ROL: [Pediatra general/Especialista específico] con [X] años de experiencia
CONTEXTO CLÍNICO: [Edad, peso, antecedentes, setting (consulta/emergencia/hospitalización)]
PRESENTACIÓN: [Motivo consulta, síntomas actuales, evolución temporal]
DATOS OBJETIVOS: [Signos vitales, examen físico, estudios disponibles]
ANÁLISIS REQUERIDO: [Diagnóstico diferencial/Plan terapéutico/Educación familiar]
FORMATO: [Estructura deseada para uso clínico inmediato]
CONSIDERACIONES: [Limitaciones, contraindicaciones, seguimiento necesario]
```

---

## Ejemplos Listos para Uso Clínico

### Para Diagnóstico Diferencial
```
Actúa como pediatra de emergencias. Analiza este caso y proporciona diagnóstico diferencial estructurado:

PACIENTE: [Edad, sexo, antecedentes relevantes]
PRESENTACIÓN: [Síntomas principales, duración, evolución]
EXAMEN FÍSICO: [Signos vitales, hallazgos positivos y negativos relevantes]

Proporciona:
1. DIAGNÓSTICOS DIFERENCIALES: Ordenados por probabilidad con justificación
2. ESTUDIOS COMPLEMENTARIOS: Qué solicitar y por qué
3. MANEJO INMEDIATO: Medidas terapéuticas urgentes si aplican
4. CRITERIOS DE DERIVACIÓN: Cuándo referenciar y a dónde
```

### Para Educación Familiar
```
Actúa como pediatra especializado en comunicación familiar. 

DIAGNÓSTICO: [Condición específica]
AUDIENCIA: [Padres primerizos/experimentados, nivel educativo, idioma]
OBJETIVO: [Explicar diagnóstico/tratamiento/prevención/seguimiento]

Crea explicación que incluya:
1. QUÉ ES: Definición en lenguaje simple
2. POR QUÉ OCURRE: Causas principales sin tecnicismos
3. TRATAMIENTO: Qué hacer, cómo y cuándo
4. SEÑALES DE ALARMA: Cuándo consultar urgente
5. PREVENCIÓN: Cómo evitar recurrencias
6. PRONÓSTICO: Qué esperar en términos comprensibles
```

### Para Revisión de Literatura
```
Actúa como pediatra investigador experto en [ESPECIALIDAD]. 

Analiza estos [N] estudios sobre [TEMA ESPECÍFICO] y proporciona:
1. SÍNTESIS METODOLÓGICA: Diseños, poblaciones, limitaciones
2. HALLAZGOS CLAVE: Resultados principales por estudio
3. NIVEL DE EVIDENCIA: Calidad y aplicabilidad clínica
4. CONTROVERSIAS: Puntos de disagreement entre estudios
5. IMPLICACIONES CLÍNICAS: Cómo aplicar en práctica pediátrica
6. GAPS DE CONOCIMIENTO: Qué falta investigar

FORMATO: Para presentación a comité médico
```

### Para Protocolos de Manejo
```
Desarrolla protocolo de manejo para [CONDICIÓN PEDIÁTRICA] considerando:

POBLACIÓN: [Grupo etario específico, comorbilidades]
SETTING: [Consulta externa/Emergencia/Hospitalización]
RECURSOS: [Estudios disponibles, medicamentos, especialistas]

Incluye:
1. CRITERIOS DIAGNÓSTICOS: Cómo confirmar diagnóstico
2. CLASIFICACIÓN DE SEVERIDAD: Leve/moderado/severo con criterios
3. ALGORITMO TERAPÉUTICO: Decisiones step-by-step
4. CRITERIOS DE HOSPITALIZACIÓN: Cuándo internar
5. SEGUIMIENTO: Cronograma de controles
6. EDUCACIÓN: Qué enseñar a familias
```

### Para Análisis de Caso Complejo
```
Actúa como [ESPECIALISTA] con experiencia en casos complejos.

CASO: [Presentación detallada del paciente]
EVOLUCIÓN: [Curso clínico, tratamientos previos, respuesta]
ESTUDIOS: [Resultados de laboratorio, imágenes, otros]

Análisis requerido:
1. REEVALUACIÓN DIAGNÓSTICA: Diagnósticos alternativos no considerados
2. PLAN DIAGNÓSTICO: Estudios adicionales necesarios
3. AJUSTE TERAPÉUTICO: Modificaciones al tratamiento actual
4. INTERCONSULTAS: Qué especialistas involucrar
5. PRONÓSTICO: Expectativas realistas
6. PLAN DE SEGUIMIENTO: Monitoreo a corto y largo plazo
```

### Para Investigación Clínica
```
Diseña estudio de investigación sobre [PREGUNTA CLÍNICA] considerando:

POBLACIÓN: [Pacientes pediátricos específicos]
SETTING: [Institucional/multicéntrico/poblacional]
RECURSOS: [Presupuesto, tiempo, personal disponible]

Proporciona:
1. PREGUNTA PICO: Población, Intervención, Comparación, Outcome
2. DISEÑO DE ESTUDIO: Tipo más apropiado y justificación
3. CRITERIOS INCLUSIÓN/EXCLUSIÓN: Bien definidos
4. TAMAÑO MUESTRAL: Cálculo con justificación estadística
5. OUTCOMES: Primarios y secundarios medibles
6. ANÁLISIS ESTADÍSTICO: Plan analítico apropiado
7. CONSIDERACIONES ÉTICAS: Aspectos específicos pediátricos
```

---

## Comparativa de Modelos para Práctica Pediátrica

### Leyenda
- **🔍 Búsqueda Médica**: Acceso a literatura médica actualizada
- **📁 Análisis Clínico**: Procesamiento de historias, imágenes médicas
- **🧠 Razonamiento Diagnóstico**: Modelos especializados en lógica médica

| **Modelo** | **Fortalezas Médicas** | **Mejor para Pediatría** | **🔍** | **📁** | **🧠** | **Precio** |
|------------|------------------------|---------------------------|---------|---------|---------|------------|
| **ChatGPT** | Razonamiento clínico, síntesis literatura | Casos complejos, educación familiar | ✅ | ✅ | ✅ | Gratis / $20/mes |
| **Claude** | Análisis extenso, ética médica | Historias largas, revisiones sistemáticas | ✅ | ✅ | ❌ | Gratis / $20/mes |
| **Grok** | Info médica tiempo real | Últimas guías, outbreak alerts | ✅ | ✅ | ✅ | $8-30/mes |
| **Gemini** | Integración Google Scholar | Búsqueda literatura, protocolos | ✅ | ✅ | ✅ | Gratis / $20/mes |
| **Meta AI** | Multimodal, imágenes | Análisis radiológico, dermatología | ✅ | ✅ | ✅ | Gratuito |
| **DeepSeek** | Lógica, análisis datos | Epidemiología, bioestadística | ✅ | ✅ | ✅ | Gratuito |

---

## Recomendaciones por Uso Clínico

**🩺 Diagnóstico Diferencial:** ChatGPT o1 > Claude > Gemini  
**📚 Revisión Literatura:** Gemini (Scholar) > ChatGPT > Claude  
**👨‍👩‍👧‍👦 Educación Familiar:** Claude > ChatGPT > Meta AI  
**📊 Análisis Datos:** DeepSeek > ChatGPT > Gemini  
**🏥 Protocolos Hospitalarios:** ChatGPT > Claude > Gemini  
**🔬 Investigación:** Gemini > ChatGPT > Claude  
**📱 Consulta Rápida:** Grok > Meta AI > ChatGPT  

---

## ⚠️ Advertencias Críticas para Uso Médico

### 🚨 NUNCA usar IA para:
- **Diagnósticos definitivos** sin evaluación clínica personal
- **Decisiones terapéuticas urgentes** sin supervisión médica
- **Dosificaciones pediátricas** sin verificar en fuentes oficiales
- **Interpretación de estudios críticos** (gases arteriales, ECG anormales)
- **Casos de emergencia** que requieren acción inmediata
- **Reemplazar anamnesis y examen físico** directo

### ✅ SÍ usar IA para:
- **Estructurar diagnósticos diferenciales** como punto de partida
- **Revisar literatura reciente** sobre temas específicos
- **Preparar material educativo** para familias
- **Analizar datos de investigación** no clínica
- **Optimizar protocolos** existentes con nueva evidencia
- **Crear contenido académico** y presentaciones

### 📋 Transparencia obligatoria:
- **Declarar uso de IA** en investigaciones y publicaciones
- **Documentar prompts utilizados** para reproducibilidad
- **Especificar modelo y versión** empleados
- **Verificar información crítica** con fuentes primarias
- **No citar IA** como fuente bibliográfica

---

## Checklist de Mejores Prácticas Médicas

### ✅ Antes de consultar IA:
- [ ] Definir objetivo clínico específico (diagnóstico/tratamiento/educación)
- [ ] Elegir modelo apropiado para el tipo de consulta
- [ ] Preparar información clínica relevante y organizada
- [ ] Considerar urgencia - ¿requiere decisión inmediata?

### ✅ Al estructurar prompts médicos:
- [ ] Especificar rol médico apropiado (pediatra general/especialista)
- [ ] Incluir contexto clínico completo (edad, peso, antecedentes)
- [ ] Proporcionar datos objetivos (signos vitales, examen físico)
- [ ] Solicitar formato apropiado para uso clínico
- [ ] Establecer limitaciones y consideraciones de seguridad

### ✅ Al recibir respuesta médica:
- [ ] Verificar recomendaciones con guidelines actuales
- [ ] Contrastar con experiencia clínica personal
- [ ] Consultar fuentes primarias para información crítica
- [ ] Evaluar aplicabilidad al contexto local/institucional
- [ ] Documentar proceso para casos complejos

### ✅ Para seguridad del paciente:
- [ ] Nunca actuar únicamente basándose en respuesta de IA
- [ ] Siempre realizar evaluación clínica independiente
- [ ] Verificar dosificaciones con fuentes oficiales
- [ ] Consultar colegas para casos complejos o inusuales
- [ ] Mantener razonamiento clínico crítico activo

---

## Consideraciones Éticas Específicas en Pediatría

### 🔴 Riesgos particulares en población pediátrica:
- **Variabilidad por edad**: Protocolos cambian drásticamente entre neonatos y adolescentes
- **Dosificaciones críticas**: Errores pueden ser fatales en pediatría
- **Desarrollo cognitivo**: Explicaciones deben adaptarse a nivel de comprensión
- **Consentimiento**: Consideraciones especiales para menores de edad
- **Privacidad**: Protección adicional de datos de menores

### 🟢 Uso responsable en pediatría:
- Verificar SIEMPRE dosificaciones pediátricas específicas
- Adaptar comunicación al desarrollo cognitivo del niño
- Incluir consideraciones familiares en planes de manejo
- Respetar autonomía progresiva en adolescentes
- Documentar consideraciones éticas en investigación pediátrica

---

## Jerarquía de Efectividad en Medicina

**De menor a mayor utilidad clínica:**
1. Prompting básico médico
2. Zero-shot con contexto clínico específico  
3. Few-shot con casos similares bien documentados
4. Chain-of-thought diagnóstico estructurado
5. **Combinación óptima:** Role-playing especializado + CoT + Contexto clínico completo

**💡 Regla de oro médica:** Más contexto clínico específico y verificación independiente = Mayor utilidad y seguridad

---

## Recursos Adicionales para Pediatras

### Fuentes de Verificación Recomendadas:
- **UpToDate Pediatrics** - Información clínica actualizada
- **PubMed** - Literatura médica primaria
- **Cochrane Library** - Revisiones sistemáticas
- **AAP Guidelines** - Recomendaciones oficiales
- **WHO/UNICEF** - Estándares internacionales pediátricos

### Comunidades y Actualización:
- **Sociedad Peruana de Pediatría** - Guidelines locales
- **Academia Americana de Pediatría** - Recursos educativos
- **Reddit r/Pediatrics** - Discusión entre colegas
- **Telegram grupos médicos** - Consultas rápidas entre especialistas

### Cursos y Certificación:
- **Verificar cada 3-6 meses** - Actualización de modelos de IA
- **Cursos de bioética en IA** - Uso responsable en medicina
- **Prompting médico especializado** - Técnicas avanzadas para clínicos

---

## Contacto y Recursos

**Ms. Nicolás Baier**  
TECMEDHUB - Universidad Austral de Chile  
**Presentación completa:** 
**Email:** david.avila@uach.cl

---

*Esta guía es material de apoyo para la presentación "Ingeniería de Prompts en Pediatría: Maximizando el Potencial de la IA en Investigación y Práctica Clínica" - Sociedad Peruana de Pediatría, Julio 2025*

**Disclaimer médico:** Esta información es para fines educativos únicamente. No constituye consejo médico profesional. Siempre consulte con profesionales médicos calificados para decisiones clínicas específicas.
