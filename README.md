# G3-TPS-Analisis-de-patrones-ictales-de-crisis-IAS-temporales-en-EEG-de-cuero-cabelludo

Este repositorio contiene el trabajo práctico de procesamiento de señales biomédicas desarrollado para la materia **Procesamiento de Señales e Imágenes Biomédicas (16.63)**. El objetivo del trabajo fue analizar señales de EEG de cuero cabelludo correspondientes a crisis IAS/FIAS de localización temporal de la **Siena Scalp EEG Database**, con foco en la caracterización de un patrón ictal compuesto por actividad delta inicial y actividad theta/alfa durante la evolución temprana de la crisis.

## Integrantes

* Valentina Haag
* Juana Rives
* Jana Yoo

## Contenido del repositorio

* `PSIB2026Q1-TPS-Grupo3-Rives_Haag_Yoo.ipynb`: notebook principal con el pipeline de procesamiento, análisis y visualización de resultados.
* `Resultados_G3_TPS.zip`: archivo comprimido con las figuras generadas durante el procesamiento.
* `README.md`: descripción general del proyecto y organización del repositorio.

## Base de datos

Se utilizó la **Siena Scalp EEG Database**, disponible públicamente en PhysioNet. La base contiene registros EEG de pacientes adultos con epilepsia, adquiridos con frecuencia de muestreo de 512 Hz y electrodos ubicados según el sistema internacional 10–20.

Por tamaño y organización, los archivos crudos de la base de datos no se incluyen en este repositorio. Para ejecutar el notebook completo, los registros EDF y los archivos de anotaciones deben descargarse desde PhysioNet y ubicarse localmente siguiendo la estructura de carpetas indicada en el notebook.

## Resumen del pipeline

El procesamiento implementado incluyó:

1. Emparejamiento de archivos EDF, anotaciones TXT y metadatos clínicos.
2. Selección de crisis IAS/FIAS de localización temporal.
3. Recorte de segmentos preictales, ictales y postictales alrededor de cada crisis.
4. Preprocesamiento adaptativo con evaluación de interferencia de línea, filtro notch cuando correspondía y filtrado pasabanda 0,5–45 Hz.
5. Control de calidad cualitativo para marcar ventanas potencialmente artefactadas.
6. Análisis espectral mediante PSD de Welch y cálculo de potencia relativa en bandas de interés.
7. Evaluación del patrón delta 1–4 Hz en 0–10 s y theta/alfa 5–9 Hz en 10–30 s.
8. Análisis temporal de amplitud mediante RMS móvil.
9. Inspección visual complementaria de ritmicidad.
10. Análisis tiempo-frecuencia mediante espectrogramas.
11. Análisis interhemisférico mediante comparación de potencia relativa en canales temporales monopolares y derivaciones bipolares.

## Resultados generados

El archivo `Resultados_G3_TPS.zip` contiene las figuras generadas por el notebook, organizadas en carpetas:

* `01_PSD_normal_log_rel/`: PSD normal, PSD logarítmica, potencia relativa por paciente y gráficos resumen del análisis espectral.
* `02_amplitud/`: curvas de RMS y comparación preictal/ictal.
* `03_lateralidad/`: resultados de lateralidad espectral monopolar y bipolar.
* `04_espectrogramas_final/`: espectrogramas ictales por paciente.
* `05_ritmicidad/`: capturas utilizadas para la inspección visual complementaria de ritmicidad.

## Librerías utilizadas

El procesamiento fue implementado en Python utilizando principalmente:

* `numpy`
* `pandas`
* `matplotlib`
* `scipy`
* `mne`
* `pathlib`
* `re`
* `datetime`

## Ejecución

Para ejecutar el notebook:

1. Descargar los registros correspondientes de la Siena Scalp EEG Database.
2. Organizar los archivos EDF y TXT en las carpetas indicadas en el notebook.
3. Abrir `PSIB2026Q1-TPS-Grupo3-Rives_Haag_Yoo.ipynb` en Google Colab o Jupyter Notebook.
4. Ejecutar las celdas en orden.
5. Revisar las figuras generadas y las tablas resumen producidas durante el análisis.

## Aclaración

El trabajo no busca realizar detección automática de crisis, predicción preictal ni diagnóstico clínico. Los resultados se interpretan como una caracterización exploratoria de patrones ictales temporales en EEG de superficie.
