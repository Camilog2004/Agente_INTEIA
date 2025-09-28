# 🚀 SECOP AI Scraper & Analyzer  

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)](https://www.python.org/)  
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-green?logo=mongodb)](https://www.mongodb.com/atlas)  
[![Gemini](https://img.shields.io/badge/Google-Gemini_AI-orange?logo=google)](https://deepmind.google/technologies/gemini/)  
[![Selenium](https://img.shields.io/badge/Selenium-Automation-brightgreen?logo=selenium)](https://www.selenium.dev/)  

---

## 🌐 Descripción General  
Este proyecto automatiza la búsqueda y análisis de **convocatorias publicadas en el SECOP II** (plataforma oficial de contratación pública en Colombia).  

Mediante **Selenium** y **BeautifulSoup**, se realiza un **web scraping estructurado** para extraer información de procesos publicados.  
Lo innovador: el proyecto incorpora **inteligencia artificial (Google Gemini)** para:  

✅ **Interpretar el contexto desestructurado** de cada convocatoria.  
✅ **Decidir automáticamente si la convocatoria es postulable o no**.  
✅ **Extraer campos clave** en un formato JSON estandarizado.  
✅ Explicar el **motivo concreto cuando no es postulable**.  

---

## ⚙️ Flujo del Proyecto  

1. **Scraping con Selenium**  
   - Automatiza la búsqueda en el portal del **SECOP II**, ingresando rangos de fechas.  
   - Recorre todas las páginas de resultados y obtiene enlaces únicos de cada convocatoria.  

2. **Visita y extracción de contenido**  
   - Accede a cada convocatoria.  
   - Limpia y normaliza el texto para análisis.  

3. **Análisis con Inteligencia Artificial**  
   - Se envía el contenido al modelo **Gemini 2.0 Flash**.  
   - Devuelve un JSON estructurado con campos clave.  

4. **Almacenamiento en Base de Datos**  
   - Se guarda en **MongoDB Atlas**, evitando duplicados mediante `idProceso`.  

---

## 🤖 Valor Diferencial  

Lo que hace único este proyecto es la **fusión de scraping + IA + almacenamiento estructurado**:  

- Otros scrapers solo descargan datos sin estructura.  
- Aquí la IA **entiende el contexto**, decide y justifica.  
- Ahorra tiempo en revisiones manuales y permite enfocarse en **oportunidades realmente relevantes**.  

---

## 🛠️ Tecnologías Usadas  

- **Python** 🐍  
- **Selenium + BeautifulSoup** → Automatización y scraping.  
- **Google Gemini** → Inteligencia Artificial para análisis contextual.  
- **MongoDB Atlas** → Base de datos en la nube.  

---

## Extensiones

- Hay una extensión de este proyecto implementando un RAG, permitiendo a la organización ampliar la base de datos al momento de
decidir si es una convocatoria postulable o no.

---

## 📊 Ejemplo de Respuesta de IA  

### ✅ Convocatoria postulable  
```json
{
  "esPostulable": true,
  "idProceso": "CO1.PCCNTR.1234567",
  "descripcion": "Adquisición de kits de primeros auxilios para instituciones educativas del municipio.",
  "fechaMaximaPostulacion": "2025-07-09",
  "departamento": "CUNDINAMARCA",
  "aspectosImportantes": [
    "Entidad contratante: Alcaldía municipal",
    "Requiere experiencia previa en suministros médicos",
    "Modalidad: Licitación abreviada",
    "Entrega en máximo 20 días"
  ],
  "urlConvocatoria": "https://community.secop.gov.co/Public/Tendering/OpportunityDetail/Index?noticeUID=xxxx"
}
```

### Convocatoria no postulable
```json
{
  "esPostulable": false,
  "motivoNoPostulable": "El proceso está restringido a MIPYMES locales con domicilio en el municipio."
}
```

