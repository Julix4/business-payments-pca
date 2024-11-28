# **Proyecto: Business Payments aplicando EDA, Análisis de Calidad de los Datos, PCA y K-means **

Este proyecto tiene como objetivo analizar la calidad de los datos y generar insights valiosos sobre el comportamiento de los clientes y las transacciones en la Business Payments. Este documento sirve para presentar los hallazgos clave a los stakeholders y proponer próximos pasos para la toma de decisiones estratégicas.

---

## **Objetivo**
Este proyecto busca identificar problemas de calidad en los datos de transacciones y clientes, además de proporcionar insights clave que optimicen la estrategia de marketing y la toma de decisiones. Se trabaja con dos datasets proporcionados por la empresa:
- **Cash Request**: Información sobre solicitudes de efectivo realizadas por los clientes.
- **Fees**: Datos relacionados con las tarifas aplicadas a las transacciones.

---

## **Estructura del Proyecto**
El repositorio está organizado en las siguientes carpetas:

- `analisis/`:
  - `01-EDA-cashrequest.ipynb`: Exploración de datos del dataset Cash Request.
  - `01-EDA-fees.ipynb`: Exploración de datos del dataset Fees.
  - `02-analisis-calidad-datos-cashrequest.ipynb`: Análisis de calidad de datos para el dataset Cash Request.
  - `02-analisis-calidad-datos-fees.ipynb`: Análisis de calidad de datos para el dataset Fees.
  - `03-Modelos-regresión-personalizados.ipynb`: Modelos iniciales de regresión personalizados.

- `dataset/`:
  - `extract-cashrequest-data analyst.csv`: Dataset crudo de Cash Request.
  - `extract-fees-data-analyst.csv`: Dataset crudo de Fees.
  - `fees-new.csv`: Dataset procesado con correcciones aplicadas.

- `informes/`:
  - `2. Informe-EDA.ipynb`: Informe con los hallazgos principales de la exploración de datos.
  - `3. Informe-analisis-calidad-datos.ipynb`: Informe con los resultados del análisis de calidad de datos.

---

## **Miembros del Equipo**
- **Julieth Vasco Bueno**
- **Gustavo Chavez**
- **Jordi Via**

---

## **Resultados del Proyecto**

### **1. Exploración de Datos (EDA)**
El EDA permitió identificar patrones iniciales en los datos y problemas críticos de calidad que afectan el análisis posterior.

**Hallazgos Clave**:

## 1. **Análisis de Cash Requests**

### Distribución de Transacciones por Estado
- **Estado Dominante:** `"money_back"` con **16,397 transacciones**, seguido por `"rejected"` con **6,568 transacciones**.
- **Implicaciones:**
  - Altas tasas de devoluciones y rechazos sugieren posibles problemas operativos, errores del usuario o políticas restrictivas.
  - Estados menos frecuentes, como `"canceled"` o `"active"`, podrían reflejar etapas específicas del ciclo de transacción.
  
**Posibles próximos pasos:** 
Investigar patrones en `"money_back"` y `"rejected"` para entender sus causas e impacto en ingresos y satisfacción del cliente.

---

### Evolución Temporal de las Transacciones
![Distribución Temporal](readme-png/image.png)

- **Tendencias Clave:**
  - **Crecimiento Inicial (Nov-May):** Incremento gradual, posiblemente asociado a una adopción temprana del servicio.
  - **Crecimiento Acelerado (Jun-Sep):** Aumento rápido en transacciones, que culmina en un pico significativo en **octubre** (~8,000 transacciones).
  - **Caída en Noviembre:** Reducción abrupta, posiblemente por datos incompletos, estacionalidad o factores externos.

**Nuestras conclusiones:**
- **Pico de Octubre:** Analizar causas (promociones, expansiones) para replicar este éxito.
- **Caída en Noviembre:** Verificar si los datos son completos o identificar causas internas/externas.

---

### Cohortes Mensuales
![Cohortes](readme-png/image.png)

- **Insights:**
  - **Frecuencia Promedio de Uso:** Aprox. 1.15 transacciones por usuario.
  - **Tendencias:** Incremento sostenido en la frecuencia promedio durante **junio-agosto 2020**, alcanzando un pico en **julio** (1.31 transacciones).
  - **Estacionalidad:** Los picos de verano podrían estar relacionados con promociones o mayor tiempo libre de los usuarios.

**Observaciones a tener en cuenta:**
- Podríamos replicar estrategias exitosas de **junio-agosto**.
- O diseñar incentivos personalizados para aumentar la frecuencia de uso en cohortes recientes.

---

### Tasa de Incidentes
![Tasa de Incidentes](readme-png/image.png)

- **Hallazgos Clave:**
  - Incremento constante desde junio (0.26%) hasta octubre (6.51%), con una reducción en noviembre (3.75%).
  - **Cohortes Críticas:** Agosto-octubre muestran tasas más altas, posiblemente debido a cambios en políticas, validaciones o problemas técnicos.

**Posibles acciones:**
- Podríamos analizar factores que impulsaron el aumento de incidentes en cohortes críticas.
- Optimizar procesos de pago para reducir rechazos y mejorar la experiencia del cliente.


---


## 2. **Análisis de Fees**

### Distribución por Tipo de Tarifa
![Distribución de Tarifas](readme-png/image.png)

- **Dominancia de `"instant_payment"`:** Representa ~53% de las tarifas, indicando una preferencia por pagos inmediatos.

---

### Ingresos por Cohorte
![Ingresos por Cohorte](readme-png/image.png)

- **Patrones Destacados:**
  - **Crecimiento Continuo:** Los ingresos aumentan consistentemente hasta octubre ($53,835).
  - **Caída en Noviembre:** Disminución a $1,335, posiblemente debido a menor madurez de la cohorte o cambios en la demanda.
  - **Explosión en Verano-Otoño:** Las cohortes de agosto a octubre muestran ingresos acelerados.

**Observaciones a considerar:**
- Podríamos analizar estrategias exitosas de cohortes lucrativas (agosto-octubre).
- O aumentar el desempeño de cohortes recientes mediante campañas personalizadas.

---

## 3. **Hallazgos Generales y Métricas Clave**

### Métricas Acumuladas
![Métricas Acumuladas](readme-png/image.png)

- **Ingreso Total:** $105,310 (noviembre 2020).
- **Total de Transacciones:** 21,061.
- **Cohortes Clave:** Junio-septiembre destacan por contribuciones significativas tanto en ingresos como en transacciones.

**Conclusiones:**
- **Crecimiento Sostenido:** El sistema muestra un comportamiento exponencial en ingresos y transacciones, con estrategias efectivas de retención y adquisición.
- **Potencial en Cohortes Recientes:** Aunque la cohorte de noviembre tiene menor contribución, su desempeño podría mejorar con tiempo y esfuerzos de retención.

---

## 4. **Posibles próximos pasos**

1. **Optimización de Procesos:**
   - Reducir tasas de rechazo y devoluciones.
   - Mejorar las políticas de pago y validación para minimizar incidentes.

2. **Análisis de Cohortes:**
   - Replicar estrategias exitosas de cohortes clave (junio-octubre).
   - Implementar incentivos específicos para aumentar la frecuencia de uso en cohortes menos activas.

3. **Calidad de Datos:**
   - Investigar columnas con valores nulos significativos para determinar su relevancia.
   - Implementar imputación de valores o eliminar variables irrelevantes.

4. **Estacionalidad y Promociones:**
   - Aprovechar patrones estacionales para diseñar campañas estratégicas.
   - Analizar los efectos de eventos externos (e.g., COVID) en el comportamiento de los usuarios.

5. **Seguimiento Financiero:**
   - Monitorear métricas clave (ingresos, transacciones, incidentes) para identificar patrones emergentes y ajustar estrategias en tiempo real.

---


**Visualizaciones**:
![alt text](readme-png/image.png)
![alt text](readme-png/image-1.png)
![alt text](readme-png/image-2.png)
![alt text](readme-png/image-3.png)
![alt text](readme-png/image-5.png)
![alt text](readme-png/image-7.png)



### **2. Análisis de Calidad de los Datos**
El análisis de calidad de los datos evaluó dimensiones clave como la integridad, consistencia, validez, unicidad y relevancia de los datos proporcionados.

**Hallazgos Clave**:
* Análisis de calidad de datos: **Cash Request**

  * **Valores faltantes:**
    Columnas significativamente afectadas: moderated_at, deleted_account_id, reimbursement_date, money_back_date, recovery_status, reco_creation, reco_last_update.
    Algunas columnas con datos parcialmente faltantes: user_id, cash_request_received_date, send_at.

  * **Estrategias de imputación:**
    * Fechas: Se completan basándose en lógicas derivadas de la columna created_at.
    * Datos categóricos: Uso del valor más frecuente o categorización específica.
    * Datos numéricos: Aplicación de métodos estadísticos como media, mediana o interpolación.

  * **Resultados esperados:**
    * Mejor consistencia temporal y categórica tras aplicar las soluciones.

* Análisis de calidad de datos: **Fees**
  
  * **Valores faltantes y patrones:**
    Alta incidencia de valores faltantes en columnas como category (~90% de datos faltantes, con valores categóricos limitados).
    Fechas relevantes (paid_at, from_date, to_date) presentan aproximadamente un 25-30% de datos faltantes.

  * **Estrategias de tratamiento:**
    Para valores categóricos, clasificación en categorías binomiales o nominales.

  * Fechas: Completadas en rangos basados en distribuciones observadas.

  * **Análisis temporal y categórico:**
    Limpieza y agrupación para generar interpretaciones más claras en análisis subsiguientes.


Basandonos en los criterios del Marco de Calidad de Datos podemos concluir:
  * **1. Integridad**
    - cash_request:
      Columnas con valores faltantes significativos: moderated_at, deleted_account_id, reimbursement_date, entre otras.
      Columnas parcialmente afectadas: user_id, cash_request_received_date, send_at.
    - fees:
      Columnas con valores faltantes significativos: category, to_date, from_date.
      Columnas parcialmente afectadas: paid_at.

    - Estrategias aplicadas:
      Imputación de fechas basada en patrones temporales.
      Clasificación binaria o nominal para valores categóricos.
      
  * **2. Consistencia**
    Correlaciones de valores faltantes indicaron dependencias claras entre columnas, lo que permitió imputar datos basándose en reglas lógicas.
    Ejemplo: Si deleted_account_id está vacío, moderated_at también tiende a estar vacío (indicando una cuenta activa).
    
  * **3. Relevancia**
    Se identificaron valores irrelevantes esperados en columnas condicionales, como moderated_at o deleted_account_id para usuarios activos.
    No se detectaron valores negativos en las columnas monetarias (amount) en ambos datasets.
    
  * **4. Validez**
    Ambos datasets cumplen con los rangos esperados en variables numéricas.
    Outliers: Detectados en columnas como amount, concentrados en valores altos (e.g., > 100), revisados para análisis posterior.
    
  * **5. Unicidad**
    No se detectaron registros duplicados en ninguno de los conjuntos de datos.

  * **6. Estructura**
    Se realizaron transformaciones clave para mejorar la calidad y preparación de los datos:
    - Codificación numérica (Label Encoding) de variables categóricas como recovery_status, type, status, entre otras.
    - Imputación de fechas faltantes en from_date y to_date basada en intervalos promedio calculados (20.38 días).
    - Creación de nuevas variables derivadas:
       - duration_days: Intervalo entre from_date y to_date.
       - time_to_payment_days: Diferencia entre paid_at y from_date.

**Visualizaciones**:

![alt text](readme-png/image-8.png)
![alt text](readme-png/image-10.png)
![alt text](readme-png/image-11.png)
![alt text](readme-png/image-12.png)
![alt text](readme-png/image-13.png)
![alt text](readme-png/image-14.png)
![alt text](readme-png/image-16.png)
![alt text](readme-png/image-17.png)
![alt text](readme-png/image-18.png)
![alt text](readme-png/image-19.png)
![alt text](readme-png/image-20.png)
![alt text](readme-png/image-21.png)
![alt text](readme-png/image-22.png)
![alt text](readme-png/image-23.png)
![alt text](readme-png/image-24.png)
![alt text](readme-png/image-25.png)
---



### **3. Modelos de Regresión**
Se desarrollaron modelos iniciales para predecir comportamientos de clientes a travez de PCA y utilizando K-means.

**Hallazgos Clave**:

  * Cluster Perfil Características principales
    - 0 Oro Altos ingresos, pagos lentos, confiables.
    - 1 Bronce Bajos ingresos, tiempos de pago moderados, confiables.
    - 2 Plata Ingresos moderados, tiempos promedio, incidentes recurrentes.
    - 3 Platino Bajos ingresos, pagos rápidos, sin incidentes.



**Visualizaciones**:

![alt text](readme-png/image-26.png)
![alt text](readme-png/image-27.png)
![alt text](readme-png/image-28.png)
![alt text](readme-png/image-29.png)
![alt text](readme-png/image-30.png)
![alt text](readme-png/image-31.png)
![alt text](readme-png/image-32.png)
![alt text](readme-png/image-33.png)
![alt text](readme-png/image-34.png)
![alt text](readme-png/image-35.png)
![alt text](readme-png/image-36.png)
![alt text](readme-png/image-37.png)
![alt text](readme-png/image-38.png)
![alt text](readme-png/image-39.png)
![alt text](readme-png/image-40.png)


---

## **Conclusión**
  * 1. Los tipos de clientes y su comportamiento son identificables mediante PCA
  * Análisis PCA y calidad de los datos:

    El análisis de componentes principales (PCA) permitió identificar patrones clave entre los clientes, segmentándolos en grupos con características similares según variables como amount, status, category, y type.

    Los principales grupos identificados incluyen:
    - Clientes regulares: Aquellos con transacciones frecuentes de montos bajos o estándar (50-100 unidades) asociados a estados active o direct_debit_sent.
    - Clientes problemáticos: Relacionados con rejected_direct_debit o transaction_declined, con montos más altos y patrones de retrasos en pagos.
    - Clientes prioritarios: Pocos pero significativos, con montos altos (superiores a 125) y asociados a categorías como instant_payment.
    
    Impacto en el negocio:
    - La segmentación basada en PCA puede ayudar a priorizar recursos, por ejemplo:
    - Implementar estrategias para reducir rechazos de débitos en el segmento problemático.
    - Ofrecer incentivos para retener a los clientes prioritarios.

  * 2. Actualizaciones masivas y retrasos
    
    Retrasos significativos entre created_at y updated_at:
    - Se detectaron registros con intervalos de hasta varios meses entre la creación y la actualización, lo cual podría ser causado por:
    - Procesos de moderación manual.
    - Inactividad del cliente antes de una acción correctiva.
    - Ineficiencias en el flujo de trabajo.
   
  * Otros valores a analizar posteriormente

    - Estatus financiero y coste de las operaciones, reduciendo los rechazos.
    - Aumento en la retención de los usuarios.
    - Picos de estacionalidad o acontecimientos económicos, para una mejor preparación en el futuro.
    - Uso de modelos predictivos para evitar rechazo o incidencias en los pagos.

---

## **Aprendizajes**
- Al realizar un análisis es necesario desde el inicio plantear las preguntas de negocio que se quieren averiguar, de esta manera el enfoque se mantiene durante el proyecto. ¡Siempre hay más insights que encontrar!
- La preparación de los datos es fundamental para la aplicación de los modelos, en ocaciones realizamos modelos que no dieron fruto, debido a un uso poco útil de los datos.
- El trabajo en equipo y el compromiso de todos los integrantes es fundamental para obtener mejores resultados.

---

## **Próximos Pasos**
1. Implementar las recomendaciones basadas en los insights generados.
2. Mejorar los modelos de predicción utilizando más datos históricos.
3. Automatizar el análisis de calidad de datos para futuros proyectos.
4. Completar información faltantes.

---
