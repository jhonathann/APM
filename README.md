# LineXpert - Automatización de Procesos de Ensamble para Vehículos Eléctricos

## Tabla de Contenidos

- [Descripción del Proyecto](#descripción-del-proyecto)
- [Integrantes](#integrantes)
- [Misión](#misión)
- [Visión](#visión)
- [Objetivos](#objetivos)
- [Productos Analizados](#productos-analizados)
- [Gestión del Proyecto](#gestión-del-proyecto)
  - [Etapas del Ensamblaje General](#etapas-del-ensamblaje-general)
- [Gestión de Automatización](#gestión-de-automatización)
  - [Proceso Actual vs Automatizado](#proceso-actual-vs-automatizado)
- [Análisis Financiero](#análisis-financiero)
  - [Presupuesto de adquisiciones (inversión inicial)](#presupuesto-de-adquisiciones-inversión-inicial)
  - [Consumo eléctrico](#consumo-eléctrico)
  - [Costos operativos anuales](#costos-operativos-anuales)
  - [Flujo de caja (basado en 700 unidades por més a 7000000 por unidad)](#flujo-de-caja-basado-en-700-unidades-por-més-a-7000000-por-unidad)
- [Celda Robotizada Propuesta](#celda-robotizada-propuesta)
- [Bibliografía](#bibliografía)
- [Enlaces Relevantes](#enlaces-relevantes)

## Descripción del Proyecto

**LineXpert** es una propuesta de solución de automatización para procesos de manufactura de vehículos eléctricos de dos ruedas (bicicletas, motos y patinetas). El objetivo del proyecto es optimizar líneas de producción a través del análisis de procesos, modelado del sistema de manufactura, evaluación económica y propuesta de celdas robotizadas.

Enlace del proyecto: [LineXpert GitHub Page](https://alejandrokno1.github.io/LineXpert/)

---

## Integrantes

- **Jhonathann Gómez** – jhagomezve@unal.edu.co
- **Julian Villalobos** – jlvillalobosj@unal.edu.co
- **Guillermo Alejandro Cano** – gacano@unal.edu.co

Estudiantes de Ingeniería Mecatrónica  
Universidad Nacional de Colombia - Sede Bogotá  
Semestre 2025-1

---

## Misión

Ser una empresa líder en Latinoamérica en el diseño e implementación de soluciones de automatización de procesos de ensamble para vehículos eléctricos de dos ruedas, impulsando una movilidad urbana sostenible, innovadora, eficiente y accesible para todos.

---

## Visión

Diseñar e implementar procesos de ensamble para vehículos eléctricos innovadores, priorizando soluciones creativas y eficientes que aseguren altos estándares de calidad, sostenibilidad y rendimiento.

---

## Objetivos

- Diseñar y optimizar procesos productivos que aumenten la eficiencia operativa.
- Medir la productividad y establecer planes de mejora continua en sistemas de producción.
- Desarrollar sistemas integrados de fabricación flexibles y de alta calidad.

---

## Productos Analizados

| Modelo               | Autonomía | Vel. Máx | Tiempo Carga | Peso    | Carga Máx |
| -------------------- | --------- | -------- | ------------ | ------- | --------- |
| **WOLF Artic**       | 45 Km     | 50 Km/h  | 8 h          | 48 kg   | 100 kg    |
| **Velocifero 2000W** | 90 Km     | 55 Km/h  | 10 h         | 124 kg  | 150 kg    |
| **Starker Avanti X** | 70 Km     | 25 Km/h  | 6 h          | 17.5 kg | 115 kg    |

---

## Gestión del Proyecto

Para realizar la gestion de el proyecto se definió la estructura del desglose de trabajo y el diagrama de gaant del proyecto como se muestra en la siguiente figura:

<img width="1741" height="913" alt="Gantt" src="https://github.com/user-attachments/assets/c2319751-b1ad-460a-bfa5-3cd234fe30d9" />

## Análisis de mercado

Realizando una investigación de diferentes fuentes, se estimaron los valres de unidades vendidas para vehículos eléctricos de dos ruedas en Colombia para el año 2024 como se muuestra en la siguiente tabla:

| Tipo de vehículo | Unidades estimadas | CAGR aprox | 10% mercado | Cantidad Mensual | Cantidad Diaria |
|------------------|---------------------|------------|--------------|------------------|------------------|
| Bicicletas       | 50.000              | 8,0%       | 5.000        | 417              | 21               |
| Scooters         | 45.000              | 8,0%       | 4.500        | 375              | 19               |
| Motos            | 30.000              | 8,0%       | 3.000        | 250              | 13               |

Y basado en el valor de la tasa compuesta de crecimiento anual se realizó una estimación para el año 2030

| Proyección | 10% mercado | Cantidad Mensual | Cantidad Diaria |
|------------|-------------|------------------|------------------|
| 79.344     | 7.934       | 661              | 33               |
| 71.409     | 7.141       | 595              | 30               |
| 47.606     | 4.761       | 397              | 20               |

En donde se puede ver el número necesario de unidades de cada uno de los productos que se debe producir diariamente para lograr tener dicha participación en el mercado.

## Gestión de Automatización

Se realizó el diagrama VSM del proceso para la moto AvantiX

<img width="784" height="436" alt="VSM_AvantiX" src="https://github.com/user-attachments/assets/b159c4f0-7bf9-499e-8624-4c2d886b8537" />

En base a dicho diagrama se realizó la simulación en plant simulation de este proceso:

<img width="1018" height="275" alt="PS_AvantiX" src="https://github.com/user-attachments/assets/da21455b-c7a2-4a82-8109-cc7babc084ae" />

Obteniendo el siguiente diagrama de uso de las estaciones

<img width="1832" height="995" alt="PS_AvantiX_stats" src="https://github.com/user-attachments/assets/36a4a0c2-6c16-4b42-8ce5-ab8b6c656f95" />

Se logra ver como se produce un claro cuello de botella en la estacionn de instalación del sistema eléctrico lo cuál genera un bloqueo de las estaciones anteriores a esta y unos elevados tiempos de espera de las estaciones posteriores.

Con base a este análisis se identificaron los siguientes problemas:

- Identificación de cuellos de botella principalmente en la estación del sistema eléctrico debido a su tiempo elevado.
- Hay estaciones cuyos procesos se realizan en serie los cuales pueden ser paralelizables.

Se definió la automatizacion del proceso haciendo principalmente la paralelización de varios procesos obteniendo el siguiente VSM y también reduciendo el tiempo del sistema eléctrico por medio de la implementacion de  dos estaciones que hagan este travbajo. También se redujo el tiempo asociado a la estacion de transporte al hacer uso de una celda robótica:

<img width="778" height="442" alt="VSM_AvantiX_opt" src="https://github.com/user-attachments/assets/23211c53-f2f4-4954-be49-c20de64120cd" />

Implementando este VSM en plant simulation:

<img width="861" height="342" alt="PS_AvantiX_opt" src="https://github.com/user-attachments/assets/e0c7b3c8-0c79-49c5-9250-861fb562bbdd" />

De donde se obtuvieron las siguientes estadisticas por estación:

<img width="1819" height="958" alt="PS_AvantiX_opt_stats" src="https://github.com/user-attachments/assets/c7800cce-5ebb-479f-bc60-fbab4f1fe03f" />

Con esto se logra ver como se incrementa notablemente los tiempos en los que las estaciones están trabajando lo cuál tendrá el efecto correspondiente en los KPI de la línea.

### Proceso Actual vs Automatizado

Se pudo entonces determinar las siguientes comparaciones para observar la mejora entre el proceso actual y el sugerido

| Producto         | Disponibilidad | Q   | Producción Actual (unds/día) | PE   | OEE    |
| ---------------- | -------------- | --- | ---------------------------- | ---- | ------ |
| Avanti X         | 0.94           | 0.8 | 8                            | 0.77 | 57.85% |
| Wolf Artic       | 0.95           | 0.8 | 12                           | 0.81 | 61.66% |
| Velocifero 2000w | 0.94           | 0.8 | 10                           | 0.85 | 64.27% |

| Producto         | Disponibilidad | Q   | Producción Actual (unds/día) | PE   | OEE |
| ---------------- | -------------- | --- | ---------------------------- | ---- | --- |
| Avanti X         | 0.94           | 0.9 | 17                           | 0.87 | 74% |
| Wolf Artic       | 0.95           | 0.9 | 19                           | 0.84 | 72% |
| Velocifero 2000w | 0.94           | 0.9 | 19                           | 0.87 | 74% |

En donde se muestra que la automatización propuesta incrementa tanto el unidades producidas por jornada, como el OEE general de la línea de ensamble.

---

# Análisis Financiero

Basado en los elementos requeridos por la propuesta de la automatización, se realizó un estimao de la inversión inicial necesaria:

## Presupuesto de adquisiciones (inversión inicial)

El cálculo de la inversión inicial se obtuvo teniendo en cuenta las 3 líneas de producción. Para los objetos a adquirir se tomaron a partir de su costo base, un costo adicional de seguro y transporte al país, constos arancelarios asumidos en 5% del valor del objeto, el IVA y otros diferentes costos logísticos lo como se muestra en la siguiente tabla:

| Item                    | Cantidad | Costo Base Unitario (USD) | Seguro y Transporte | Arancel (5%) | IVA     | Costos Logísticos | Costo Total Unitario (USD) | Costo Total (USD) | Costo Total (COP)     |
|-------------------------|----------|----------------------------|----------------------|--------------|---------|--------------------|-----------------------------|--------------------|------------------------|
| Robot                   | 3        | $27.500                    | $1.075               | $1.375       | $5.225  | $1.000             | $36.175                     | $108.525           | $488.362.500           |
| Bandas Transportadoras  | 30       | $7.000                     | $460                 | $350         | $1.330  | $1.000             | $10.140                     | $304.200           | $1.368.900.000         |
| Grippers                | 3        | $2.700                     | $331                 | $135         | $513    | $1.000             | $4.679                      | $14.037            | $63.166.500            |
| Sensores                | 30       | $80                        | $252                 | $4           | $15     | $1.000             | $1.352                      | $40.548            | $182.466.000           |
| PLC, Sistema de Control | 3        | $500                       | $265                 | $25          | $95     | $1.000             | $1.885                      | $5.655             | $25.447.500            |
| Elementos de Seguridad  | 3        | $2.000                     | $310                 | $100         | $380    | $1.000             | $3.790                      | $11.370            | $51.165.000            |
| Costos de instalación   | 3        | $5.000                     | -                    | -            | -       | $1.000             | $6.950                      | $20.850            | $93.825.000            |
| Honorarios              | 1        | -                          | -                    | -            | -       | -                  | -                           | -                  | $10.676.250            |
| **Total**               |          |                            |                      |              |         |                    |                             |                    | **$2.284.008.750**     |

El cálculo de los honorarios se obtuvo a partir de la recomendación de la ACIEM en su manual de tarifas de referencias en ingeniería como se muestra a continuación:

| Escalafón | SMMLV | Horas/mes | Total (COP) | Total/h (COP) |
|-----------|-------|-----------|--------------|----------------|
| 7         | 5     | 160       | $7,117,500   | $44,484        |

| Cantidad | Costo/hora | Horas Totales | Total cant | Total       |
|----------|------------|----------------|-------------|-------------|
| 3        | $44.484    | 80             | $3.558.750  | $10.676.250 |

## Ingresos

Basado en las ventas anuales estimadas se estimaron los ingresos anuales brutos, y netos después de impuestos.

| Modelo           | Precio Unidad       | Producción Diaria | Cantidad Mensual | Cantidad Anual | Ingreso Anual Bruto   | Ingreso Anual Neto     |
|------------------|---------------------|-------------------|------------------|----------------|-----------------------|------------------------|
| Avanti X         | $6.000.000,00       | 17                | 340              | 4.080          | $24.480.000.000       | $20.571.428.571        |
| Wolf Artic       | $3.800.000,00       | 19                | 380              | 4.560          | $17.328.000.000       | $14.561.344.538        |
| Velocífero 2000  | $7.500.000,00       | 18                | 360              | 4.320          | $32.400.000.000       | $27.226.890.756        |
| **Total Anual**  |                     |                   |                  | **12.960**     | **$74.208.000.000**   | **$62.359.663.866**    |

## Costos operativos anuales

Los costos operativos anuales se describen en la siguiente tabla, en dónde se consideraron los Insumos necesarios para ensamblar cada parte, La energía eléctrica consumida por el sistema, Los salarios de los operarios y el mantenimiento preventivo general.

| Rubro               | Costo Anual (COP)     |
|---------------------|------------------------|
| Insumos             | $59.230.800.000        |
| Energía Eléctrica   | $27.720.000            |
| Salarios Operarios  | $1.798.548.576         |
| Mantenimientos      | $129.375.000           |
| **Total**           | **$61.186.443.576**    |


### Insumos

Se realizó un estimado de los insumos necesario para el ensamble de cada uno de los productos

#### AvantiX

| Material     | Precio (COP) |
|--------------|--------------|
| Chasis       | $500.000     |
| Motor        | $1.000.000   |
| Batería      | $800.000     |
| Circuitería  | $400.000     |
| Ruedas       | $500.000     |
| Suspensión   | $300.000     |
| Frenos       | $400.000     |
| Manubrio     | $400.000     |
| Luces        | $200.000     |
| Sillín       | $150.000     |
| Accesorios   | $200.000     |
| **Total**    | **$4.850.000** |

#### Wolf Artic

| Material     | Precio (COP) |
|--------------|--------------|
| Cuadro       | $300.000     |
| Motor        | $600.000     |
| Batería      | $400.000     |
| Circuitería  | $300.000     |
| Ruedas       | $400.000     |
| Pedaleo      | $200.000     |
| Frenos       | $300.000     |
| Manubrio     | $200.000     |
| Luces        | $150.000     |
| Sillín       | $180.000     |
| Accesorios   | $125.000     |
| **Total**    | **$3.155.000** |

####

| Material     | Precio (COP) |
|--------------|--------------|
| Chasis       | $600.000     |
| Motor        | $1.100.000   |
| Batería      | $1.000.000   |
| Circuitería  | $400.000     |
| Ruedas       | $800.000     |
| Suspensión   | $300.000     |
| Frenos       | $400.000     |
| Manubrio     | $500.000     |
| Luces        | $300.000     |
| Sillín       | $200.000     |
| Accesorios   | $300.000     |
| **Total**    | **$5.800.000** |

#### Total

Basado  en estos estimados se tiene el costo de insumos Anual estimado

| Modelo           | Cantidad Producida | Costo Anual (COP)     |
|------------------|--------------------|------------------------|
| Avanti X         | 4.080              | $19.788.000.000        |
| Wolf Artic       | 4.560              | $14.386.800.000        |
| Velocífero       | 4.320              | $25.056.000.000        |
| **Total**        | **12.960**         | **$59.230.800.000**    |

### Energia Eléctrica

Se realizó un estimado de la energía eléctrica consumida comose muestra en la siguiente tabla asumiento un costo de kWh de 308 pesos:

| Máquina                | Cantidad | Consumo/Día unidad (kWh) | Consumo Total/Día (kWh) | Consumo Mensual | Consumo Anual | Costo Anual (COP) |
|------------------------|----------|---------------------------|--------------------------|------------------|----------------|--------------------|
| Robot ABB              | 3        | 40                        | 120                      | 2400             | 28800          | $8.870.400         |
| Bandas Transportadoras | 30       | 8                         | 240                      | 4800             | 57600          | $17.740.800        |
| Adicional              | 3        | 5                         | 15                       | 300              | 3600           | $1.108.800         |
| **Total**              |          |                           |                          |                  |                | **$27.720.000**    |

### Salario Operarios

Basado en su rol se fijo un salio para los operarios involucrados que van de 2 a 3 SMMLV

| Rol        | Cantidad Trabajadores | SMMLV | Costo Mensual     | Costo Anual         |
|------------|------------------------|-------|--------------------|----------------------|
| Operario   | 28                     | 2     | $135.374.624       | $1.624.495.488       |
| Supervisor | 2                      | 3     | $14.504.424        | $174.053.088         |
| **Total**  |                        |       |                    | **$1.798.548.576**   |


### Mantenimientos Preventivos

Para garantizar la vida útil de los equipos y el correcto funcionamiento de las líneas de producción se estimaron los costos de los mantenimientos preventivos de los equipos

| Ítem                 | Cantidad | Costo Anual Unitario (USD) | Costo Anual (USD) | Costo Anual (COP)    |
|----------------------|----------|-----------------------------|-------------------|-----------------------|
| Robots               | 3        | $2,500                      | $7,500            | $33,750,000           |
| Banda Transportadora | 30       | $600                        | $18,000           | $81,000,000           |
| Gripper              | 3        | $150                        | $450              | $2,025,000            |
| Sensor               | 30       | $30                         | $900              | $4,050,000            |
| PLC                  | 3        | $300                        | $900              | $4,050,000            |
| Otros                | 1        | $1,000                      | $1,000            | $4,500,000            |
| **Total**            |          |                             |                   | **$129,375,000**      |


## Flujo de caja

Con los valores para ingresos y costos obtenidos anteriormente se obtuvo el flujo de caja para los 5 primeros años de la inversión

| Año | Ingresos           | Costos             | Inversión         | Flujo Neto         |
|-----|--------------------|--------------------|--------------------|--------------------|
| 0   | $0                 | $0                 | -$2.284.008.750   | -$2.284.008.750    |
| 1   | $62.359.663.866    | -$61.186.443.576   | $0                | -$1.110.788.460    |
| 2   | $62.359.663.866    | -$61.186.443.576   | $0                | $62.431.829        |
| 3   | $62.359.663.866    | -$61.186.443.576   | $0                | $1.235.652.119     |
| 4   | $62.359.663.866    | -$61.186.443.576   | $0                | $2.408.872.408     |
| 5   | $62.359.663.866    | -$61.186.443.576   | $0                | $3.582.092.698     |

## Indicadores de inversión

Del flujo de caja enterior podemos obtener la tasa interna de retorno y compararla con otras alternativas de inversión

| Concepto          | Valor |
|-------------------|-------|
| TIR               | 21%   |
| CDT               | 10%   |
| FIC medio riesgo  | 13%   |
| FIC alto riesgo   | 17%   |

En donde se muestra que la tasa puede competir con estas alternativas de inversión incluso cuando se habla de fondos de inversión colectiva de mayor riesgo los cuales tienen asociadas mayores rentabildiades efectivas anuales. También se obtienen otros indicadores de la inversión como el VPN el cuál al ser positivo indica la favorabilidad de la inversión, y el payback de la inversión que es de 2 años por lo que la inversion se recupera rápidamente. Se tiene por último el ROI de 57% indicando nuevamente la favorabilidad de la inversión.

| Indicador   | Valor                   |
|-------------|--------------------------|
| VPN         | $1.555.633.841,39        |
| Payback     | 2                        |
| ROI 5 años  | 57%                      |

---

## Celda Robotizada Propuesta

### Funcionalidad

- Pick & Place: traslado del chasis a la banda
- Ensamble automático del motor con control de torque

### Valor Agregado

- Reducción del tiempo de ciclo
- Aumento de la precisión y calidad
- Mejora en seguridad del operario

### Seguridad Funcional

- Paros de emergencia
- Mallas y sensores de presencia

### Efector Final

- Garra neumática ajustable
- Ventosas y sistema de atornillado

---
## Digital Factory / Controladores Industriales y SCADA

El video explicativo realizado de toda esta sección se encuentra a continuación

[![Miniatura del video](https://img.youtube.com/vi/7de41F2nmR0/0.jpg)](https://youtu.be/7de41F2nmR0)

---
## Bibliografía

- Módulos de clase de manufactura robotizada – UNAL 2025
- ABB, Motoman, Ripipsa, SMC – Catálogos industriales de robots y grippers
- Manual ACIEM de tarifas 2015
- Noticias del mercado energético y movilidad eléctrica en Colombia

---

## Enlaces Relevantes
- [Página Web del Proyecto](https://jlvillalobosj.wixsite.com/linexpert2)
  
- [Página GitHub del Proyecto](https://github.com/jhonathann/APM)
  
- [Video en YouTube sección SCADA/PLC/Digital Factory](https://youtu.be/7de41F2nmR0)

- [Video de la presentación final](https://www.youtube.com/watch?v=RsAYxRpVNy4)


