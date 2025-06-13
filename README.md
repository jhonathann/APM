# LineXpert - Automatización de Procesos de Ensamble para Vehículos Eléctricos

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

##  Visión

Diseñar e implementar procesos de ensamble para vehículos eléctricos innovadores, priorizando soluciones creativas y eficientes que aseguren altos estándares de calidad, sostenibilidad y rendimiento.

---

## Objetivos

- Diseñar y optimizar procesos productivos que aumenten la eficiencia operativa.
- Medir la productividad y establecer planes de mejora continua en sistemas de producción.
- Desarrollar sistemas integrados de fabricación flexibles y de alta calidad.

---

## Productos Analizados

| Modelo        | Autonomía | Vel. Máx | Tiempo Carga | Peso | Carga Máx |
|---------------|-----------|----------|---------------|------|-----------|
| **WOLF Artic**     | 45 Km    | 50 Km/h  | 8 h           | 48 kg | 100 kg    |
| **Velocifero 2000W** | 90 Km    | 55 Km/h  | 10 h          | 124 kg| 150 kg    |
| **Starker Avanti X** | 70 Km    | 25 Km/h  | 6 h           | 17.5 kg| 115 kg   |

---

## Gestión del Proyecto
Para realizar la gestion de el proyecto se definió la estructura del desglose de trabajo y el diagrama de gant del proyecto como se muestra en la siguiente figura:

![Gant](https://github.com/user-attachments/assets/f1ccfc06-13b4-4d6e-9c65-ce56424b5c93)

### Etapas del Ensamblaje General

De acuerdo a la investigación estas son, en general, las etapas de ensamblaje de los productos

1. Preparación del chasis  
2. Montaje del motor a la rueda trasera  
3. Montaje de ruedas y frenos al chasis  
4. Montaje del manubrio y periféricos  
5. Instalación eléctrica y cableado  
6. Montaje de luces, sillín y accesorios  
7. Pruebas de verificación  

---

## Gestión de Automatización

Se realizó el diagrama VSM del proceso para la moto ArtiX

![VSM_AvantiX](https://github.com/user-attachments/assets/8ef9a46e-dc7e-4e75-8078-0f6b311b8cc9)

En base a dicho diagrama se realizó la simulación en plant simulation de este proceso
![PS_AvantiX](https://github.com/user-attachments/assets/ec6b64f4-a7c9-4e0f-a08c-b3351b9948c0)

Obteniendo el siguiente diagrama de uso de las estaciones

![PS_AvantiX_stats](https://github.com/user-attachments/assets/91e46e23-9fb8-4c13-9b6c-69fa2365473b)

Con base a este análisis se identificaron los siguientes problemas:

- Diagnóstico de procesos con OEE < 40% (baja eficiencia).
- Identificación de cuellos de botella en sistema eléctrico y montaje de motor.
- Diseño de celdas robotizadas Pick & Place y atornillado.
- Criterios de selección de robots, grippers y sistemas de seguridad.


Se definió la automatizacion del proceso haciendo principalmente la paralelización de varios procesos obteniendo el siguiente VSM:
![VSM_AvantiX_opt](https://github.com/user-attachments/assets/58fea508-120d-48d9-b60b-163b5021c63a)

Implementando este VSM en plant simulation:

![PS_AvantiX_opt](https://github.com/user-attachments/assets/154fbc3c-627e-4bd1-8169-6fe2daae30a0)

De donde se obtuvo:

![PS_AvantiX_opt_stats](https://github.com/user-attachments/assets/6e8ead5c-d56d-4a1d-b022-6aeb68d08110)

### Proceso Actual vs Automatizado

Se pudo entonces determinar las siguientes comparaciones para observar la mejora entre el proceso actual y el sugerido

| Producto         | Disponibilidad | Q   | Producción Actual (unds/día) | PE   | OEE     |
|------------------|----------------|-----|-------------------------------|------|---------|
| Avanti X         | 0.94           | 0.8 | 22                            | 0.46 | 34.47%  |
| Wolf Artic       | 0.95           | 0.8 | 31                            | 0.52 | 39.27%  |
| Velocifero 2000w | 0.94           | 0.8 | 25                            | 0.52 | 39.17%  |


| Producto         | Disponibilidad | Q   | Producción Actual (unds/día) | PE   | OEE   | Aumento Producción |
|------------------|----------------|-----|-------------------------------|------|-------|---------------------|
| Avanti X         | 0.94           | 0.9 | 35                            | 0.73 | 62%   | 59.1%               |
| Wolf Artic       | 0.95           | 0.9 | 43                            | 0.72 | 61%   | 38.7%               |
| Velocifero 2000w | 0.94           | 0.9 | 33                            | 0.69 | 58%   | 32%                 |



| Producto         | OEE Actual | OEE Aut. | Mejora en Producción |
|------------------|------------|----------|------------------------|
| Avanti X         | 34.47%     | 59.1%    | +62%                   |
| WOLF Artic       | 39.27%     | 61%      | +38.7%                 |
| Velocifero 2000W | 39.17%     | 58%      | +32%                   |

---

## Análisis Financiero
Basado en los elementos requeridos por la propuesta de la automatización, se realizó un estimao de la inversión inicial necesaria:

# Presupuesto de adquisiciones (inversión inicial)

| Ítem                                 | Cantidad | Costo Unitario (USD) | Costo Total (USD) | Costo Total (COP)     |
|--------------------------------------|----------|-----------------------|--------------------|------------------------|
| Robot 1 Pick & Place                 | 1        | 27,057                | 27,057             | $111,420,726.00        |
| Robot 2 Ensamblador                 | 1        | 32,000                | 32,000             | $131,776,000.00        |
| Herramientas (grippers, sensores)   | 2        | 2,913                 | 5,826              | $23,991,468.00         |
| Banda transportadora                | 1        | 7,000                 | 7,000              | $28,826,000.00         |
| Sistema neumático                   | 1        | 438                   | 438                | $1,803,684.00          |
| Elementos de seguridad (cercas, indicadores) | 1 | 2,000         | 2,000              | $8,236,000.00           |
| PLC, Sistema de Control             | 1        | 8,139                 | 8,139              | $33,516,402.00         |
| Costos de instalación               | -        | -                     | 2,000              | $8,236,000.00          |
| **Total inversión inicial**         | **8**    | **79,547**            | **84,460**         | **$347,806,280.00**    |

Se estimó también el consumo eléctrico utilizado por el brazo robótico y las bandas transportadoras

# Consumo eléctrico

|                        | kw-Hora | kw-Día | kw-Mes | Precio unitario     | Cantidad Maquinaria | Gasto mensual COP     |
|------------------------|---------|--------|--------|----------------------|----------------------|------------------------|
| Energía eléctrica      | 288 COP | 2304 COP | 46080 |                      |                      |                        |
| Brazo robótico         | $0.80   | $6.40  | $128.00 | $5,898,240.00        | 2                    | $11,796,480.00         |
| Banda Transportadora   | 0.5     | 4      | 80     | $3,686,400.00        | 3                    | $11,059,200.00         |
| Herramientas           | 1       | 8      | 160    | $7,372,800.00        | 5                    | $36,864,000.00         |
| **Total mensual**      | 2.3     | 18.4   | 46448  | 16957440             | 10                   | $59,719,680.00         |
| **Total anual**        | 27.6    | 220.8  | 557376 | 203489280            | 120                  | $716,636,160.00        |

Esto conlleva los siguientes costos anuales

# Costos operativos anuales

| Concepto                      | Monto Anual (COP)        |
|------------------------------|--------------------------|
| Energía eléctrica            | $716,636,160.00          |
| Sueldos operarios (10 operarios) | $341,640,000.00     |
| Mantenimiento robots         | $2,500,000.00            |
| Insumos                      | $2,500,000,000.00        |
| Transporte                   | $20,000,000.00           |
| **Total operativo**          | **$3,580,776,160.00**    |

Por último se realizó el analisis del flujo de caja  para la implementación general del proyecto de donde se observa que tan solo en 1 año se podrían ver utilizades sobre la inversion

# Flujo de caja (basado en 700 unidades por més a 7.000.000 por unidad)

| Año | Ingreso (COP)         | Costos operativos (COP) | Inversión (COP)     | Flujo neto (COP)         |
|-----|------------------------|--------------------------|----------------------|---------------------------|
| 0   | 0                      | 0                        | -$323,921,880.00     | -$323,921,880.00          |
| 1   | $58,800,000,000.00     | -$3,580,776,160.00       | -$323,921,880.00     | $54,571,380,080.00        |
| 2   | $58,800,000,000.00     | -$3,580,776,160.00       | $0.00                | $109,790,603,920.00       |
| 3   | $58,800,000,000.00     | -$3,580,776,160.00       | $0.00                | $165,009,827,760.00       |

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

## Bibliografía

- Módulos de clase de manufactura robotizada – UNAL 2025  
- ABB, Motoman, Ripipsa, SMC – Catálogos industriales de robots y grippers  
- Manual ACIEM de tarifas 2015  
- Noticias del mercado energético y movilidad eléctrica en Colombia  

---

## Enlaces Relevantes

- [Página GitHub del Proyecto](https://alejandrokno1.github.io/LineXpert/)
- [Catálogo ABB](https://outerreeftech.com/collections/abb-industrial-robots)
- [Grippers para robots – Ripipsa](https://ripipsa.com/grippers-robot/)
- [SMC Grippers PDF](https://static.smc.eu/pdf/Grippers%20for%20Collaborative%20Robots_EU.pdf)

---


