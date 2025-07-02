# Prompts para Presentación: Ingeniería de Prompts en Pediatría
**Sociedad Peruana de Pediatría - 16:45 a 17:30 hrs**

---

## 1. Intro: Ejemplo Comparativo PubMed vs GPT

### Búsqueda PubMed (mostrar en pantalla):
```
("fever"[MeSH] AND "infant"[MeSH] AND "diagnosis"[Subheading]) 
AND ("emergency service, hospital"[MeSH]) 
Filters: Age 0-2 years, Last 5 years, Systematic Reviews
```
*Resultado esperado: Lista de 47 papers para leer individualmente*

### GPT Optimizado (ejecutar en vivo):
```
Actúa como pediatra de emergencias con 10 años de experiencia. 

Lactante de 2 meses, previamente sano, presenta fiebre de 38.5°C sin foco aparente. 
Padres primerizos muy ansiosos. Sin síntomas respiratorios, gastrointestinales o neurológicos evidentes.

Proporciona:
1. PROTOCOLO DE EVALUACIÓN URGENTE: Pasos inmediatos en consulta
2. ESTUDIOS COMPLEMENTARIOS: Qué solicitar según edad y presentación  
3. CRITERIOS DE HOSPITALIZACIÓN: Cuándo internar vs manejo ambulatorio
4. COMUNICACIÓN FAMILIAR: Explicación en lenguaje simple para padres ansiosos
5. SEGUIMIENTO: Cuándo revaluar y señales de alarma

Formato: Estructura clara para uso inmediato en emergencias.
```

---

## 2. Tipos de Prompting - Ejemplos Rápidos

### 2.1 Prompting Básico
```
Define síndrome de muerte súbita del lactante según criterios actuales.
```

### 2.2 Zero-Shot Prompting  
```
Analiza las ventajas y limitaciones de la telemedicina en consultas pediátricas. 
Estructura tu respuesta considerando: eficacia diagnóstica, satisfacción familiar, 
limitaciones técnicas, y recomendaciones para implementación.
```

### 2.3 Few-Shot Prompting
```
Clasifica estos síntomas por urgencia pediátrica:

Ejemplo 1: "Lactante 3 meses con fiebre 39°C" → URGENCIA ALTA
Ejemplo 2: "Niño 5 años con tos seca por 2 días" → URGENCIA BAJA  
Ejemplo 3: "Adolescente con dolor abdominal y vómitos" → URGENCIA MODERADA

Ahora clasifica:
- "Recién nacido con ictericia hasta escleras"
- "Niña 8 años con cefalea y rigidez nucal"
- "Lactante 6 meses con diarrea líquida abundante"
```

### 2.4 Chain-of-Thought (CoT)
```
Evalúa este protocolo de bronquiolitis paso a paso:

"Protocolo propuesto: Todo lactante menor de 6 meses con bronquiolitis 
debe hospitalizarse. Tratamiento: salbutamol nebulizado cada 4 horas, 
corticoides orales por 5 días, antibióticos profilácticos."

Analiza paso a paso:
1) Criterios de hospitalización propuestos
2) Evidencia científica para cada tratamiento  
3) Posibles efectos adversos
4) Alternativas basadas en evidencia actual
5) Recomendaciones finales
```

### 2.5 Role-Playing
```
Actúa como neonatólogo experto en cuidados intensivos. Evalúa esta conducta:

"RN de 34 semanas con dificultad respiratoria leve. Equipo propone 
intubar profilácticamente antes del deterioro."

Proporciona tu criterio especializado sobre:
- Indicaciones actuales de intubación en prematuros
- Riesgos vs beneficios de intubación profiláctica
- Alternativas de soporte respiratorio no invasivo
- Criterios de monitoreo para decidir escalamiento
```

## Ejemplo de Meta-Prompting Pediátrico

**Tu necesidad clínica:**
*"Necesito analizar varios estudios sobre bronquiolitis en lactantes para actualizar nuestro protocolo hospitalario"*

**Meta-prompt:**
```
Soy pediatra y necesito analizar 8 estudios recientes sobre manejo de bronquiolitis 
en lactantes menores de 6 meses para actualizar nuestro protocolo hospitalario. 

Crea un prompt efectivo que me permita extraer de cada estudio:
- Criterios de hospitalización utilizados
- Intervenciones terapéuticas evaluadas  
- Outcomes primarios medidos
- Recomendaciones para práctica clínica
- Nivel de evidencia

El resultado debe ser útil para presentar al comité médico.
```

**Resultado**: La IA te diseña el prompt perfecto para tu análisis específico


---


## 3. Demostración 1: Análisis de Literatura Pediátrica

### Prompt Principal (12 minutos):
```
Actúa como pediatra investigador experto en telemedicina pediátrica. 

Analiza estos 3 abstracts sobre efectividad de teleconsultas en pediatría y proporciona:

1. METODOLOGÍAS UTILIZADAS: Diseño de estudios, poblaciones, y métricas evaluadas
2. HALLAZGOS CLAVE POR ESTUDIO: Resultados principales en eficacia diagnóstica y satisfacción
3. LIMITACIONES IDENTIFICADAS: Barreras técnicas, poblacionales y clínicas reportadas  
4. SÍNTESIS DE EVIDENCIA: Qué sabemos con certeza sobre telemedicina pediátrica
5. IMPLICACIONES CLÍNICAS: Cómo aplicar estos hallazgos en práctica pediátrica actual
6. GAPS DE INVESTIGACIÓN: Aspectos que requieren estudios adicionales

FORMATO: Estructura para presentación a comité médico de hospital pediátrico.
AUDIENCIA: Pediatras que evalúan implementar programa de telemedicina.

[Insertar los 3 abstracts preparados sobre telemedicina pediátrica]
```

### Evolución del Prompt en Tiempo Real:

**Versión 1 (mala):**
```
Resume estos estudios sobre telemedicina
```

**Versión 2 (mejorada):**
```
Analiza la efectividad de telemedicina en pediatría según estos estudios
```

**Versión 3 (optimizada - usar la de arriba):**
*El prompt principal completo*

---

## 4. Demostración 2: Caso Clínico Pediátrico

### Prompt de Caso Complejo (10 minutos):
```
Actúa como pediatra de emergencias con 15 años de experiencia en diagnóstico de enfermedades exantemáticas. 

Analiza este caso paso a paso usando razonamiento clínico estructurado:

CASO CLÍNICO:
Paciente: Niña de 4 años, previamente sana, sin antecedentes relevantes
Motivo de consulta: Fiebre y exantema por 3 días

PRESENTACIÓN CLÍNICA:
- Fiebre: 39.2°C persistente por 3 días, no responde completamente a antipiréticos
- Exantema: Maculopapular generalizado, iniciado en tronco, se extendió a extremidades
- Conjuntivitis: Bilateral, no purulenta, con inyección conjuntival marcada
- Mucosas: Labios rojos, secos y fisurados; lengua aframbuesada
- Adenopatías: Cervical anterior unilateral, firme, 2 cm, no dolorosa
- Estado general: Irritable, pero consciente y orientada
- Sin síntomas respiratorios, gastrointestinales o neurológicos

ANÁLISIS REQUERIDO paso a paso:

Paso 1: SISTEMATIZACIÓN - Lista todos los signos y síntomas por aparatos/sistemas
Paso 2: DIAGNÓSTICOS DIFERENCIALES - Mínimo 5 posibilidades, ordenados por probabilidad  
Paso 3: ESTUDIOS COMPLEMENTARIOS - Qué solicitar prioritariamente y por qué
Paso 4: CRITERIOS DIAGNÓSTICOS - Qué criterios específicos evaluar para el diagnóstico más probable
Paso 5: MANEJO INMEDIATO - Plan terapéutico y monitoreo en las próximas 24 horas
Paso 6: CRITERIOS DE DERIVACIÓN - Cuándo solicitar interconsulta y a qué especialidad
Paso 7: EDUCACIÓN FAMILIAR - Explicación del cuadro y signos de alarma para los padres

IMPORTANTE: Muestra tu razonamiento clínico explícito para cada paso.
```

### Comparación de Técnicas (mostrar diferencias):

**Zero-shot simple:**
```
¿Cuál es el diagnóstico más probable para esta niña de 4 años con fiebre y exantema?
```

**Few-shot con ejemplos:**
```
Analiza casos pediátricos siguiendo estos ejemplos:

Caso 1: Niño 3 años - Fiebre + exantema + conjuntivitis + labios fisurados = Enfermedad de Kawasaki
Caso 2: Niña 5 años - Fiebre + adenopatías + exantema macular = Mononucleosis (EBV)
Caso 3: Niño 2 años - Fiebre + exantema + tos + conjuntivitis = Sarampión

Ahora analiza: [caso de la niña de 4 años con todos los detalles]
```

---

## 5. Meta-Prompting

### Ejemplo Teórico:
```
Soy pediatra y necesito analizar 8 estudios recientes sobre manejo de bronquiolitis 
en lactantes menores de 6 meses para actualizar nuestro protocolo hospitalario. 

Crea un prompt efectivo que me permita extraer de cada estudio:
- Criterios de hospitalización utilizados
- Intervenciones terapéuticas evaluadas (broncodilatadores, corticoides, etc.)
- Outcomes primarios medidos (días de hospitalización, saturación, etc.)
- Recomendaciones para práctica clínica
- Nivel de evidencia y calidad metodológica

El resultado debe ser útil para presentar al comité médico y debe permitir 
comparación directa entre estudios.
```

### Demostración Práctica Meta-Prompting:
```
Soy pediatra y necesito crear material educativo sobre introducción de alimentación 
complementaria para padres de lactantes de 6 meses. 

El material debe ser:
- Científicamente preciso según recomendaciones actuales de OMS/AAP/SPP
- Fácil de entender para padres con diferentes niveles educativos  
- Incluir cronología de introducción de alimentos
- Mencionar señales de alerta que requieren consulta pediátrica
- Formato de guía práctica que puedan imprimir y conservar
- Considerar contexto cultural peruano

Diseña un prompt efectivo que me genere este material educativo completo y práctico.
```

**Luego ejecutar el prompt que genere la IA**

---

## Notas para el Presentador

### Timing por Sección:
- **Intro (PubMed vs GPT)**: 2-3 minutos máximo
- **Tipos de prompting**: Mostrar ejemplos rápidos, no ejecutar todos (5-7 minutos)
- **Demo 1 (Literatura)**: Ejecutar prompt completo (12 minutos)
- **Demo 2 (Caso clínico)**: Ejecutar prompt principal + mostrar diferencias (10 minutos)
- **Meta-prompting**: Ejecutar demostración práctica (5-8 minutos)

### Tips de Ejecución:
- **Copiar y pegar** directamente desde este documento
- **Tener backup** de respuestas por si falla conexión
- **Comentar en tiempo real** mientras aparecen los resultados
- **Enfatizar las diferencias** entre técnicas
- **Preguntar a la audiencia** qué notan diferente en cada respuesta

### Material de Respaldo:
- **Casos clínicos adicionales** si sobra tiempo
- **Ejemplos más simples** si la audiencia se ve perdida
- **Preguntas frecuentes** sobre limitaciones de IA en medicina

---

## Recordatorios Finales

✅ **Siempre mencionar**: "La IA complementa, no reemplaza el juicio clínico"

✅ **Enfatizar**: Verificar información crítica con fuentes primarias

✅ **Recordar**: Estos son ejemplos didácticos, no recomendaciones médicas definitivas
