# Análisis Forense y Seguridad en el Procesamiento de Contenedores Anidados en un Entorno de LLM a Gran Escala

Este repositorio presenta un estudio de caso técnico y una Prueba de Concepto (PoC) centrada en el análisis de archivos binarios, inspección de *magic bytes* y validación de seguridad durante la extracción de contenedores anidados en un **Entorno de LLM a Gran Escala**.

## 📌 Alcance y Objetivos
* **Inspección de Binarios:** Identificación y extracción recursiva de archivos con extensiones no reconocidas o ausentes que encapsulan estructuras `.zip` encadenadas.
* **Análisis de Ingeniería:** Evaluación del comportamiento del sistema durante el procesamiento de flujos de datos desconocidos dentro de un entorno aislado (*sandbox*).
* **Evaluación de Seguridad:** Análisis conceptual de la resistencia frente a vulnerabilidades de *Path Traversal* (*Zip Slip*) en rutinas de descompresión.

## 🛠️ Metodología Aplicada
1. **Identificación por Magic Bytes:** Detección de firmas de archivos directamente desde las cabeceras de bytes (`PK\x03\x04`), superando las limitaciones de nombres de archivo o extensiones.
2. **Desempaquetado Recursivo:** Procesamiento de contenedores multinivel para extraer estructuras comprimidas internas.
3. **Análisis de Validación de Rutas:** Evaluación de los controles de sanitización del sistema de archivos. En entornos seguros, la restricción del carácter separador de directorio (`/`) evita la navegación no autorizada fuera del directorio de destino.

## 🛡️ Consideraciones de Seguridad (Mitigación de Zip Slip)
Aunque los componentes de extracción de archivos pueden ser vulnerables a ataques de tipo *Zip Slip* si no sanitizan rutas relativas, el entorno evaluado mitiga eficazmente este riesgo al restringir caracteres de navegación de directorio (`/`), garantizando la escritura segura dentro del área designada.

## 📄 Uso Ético
Este material se publica exclusivamente con fines educativos, de investigación en ciberseguridad y demostración de competencias profesionales.
