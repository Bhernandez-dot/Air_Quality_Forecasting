# Air Quality Forecasting
Proyecto de curso MA5201: Aprendizaje de máquinas.

Base de datos obtenida del repositorio de bases de datos dedicados al aprendizaje de máquinas de la Universidad Pública de Irvine, California. https://archive.ics.uci.edu/ml/datasets/Air+quality.

### Data Set Information:

The dataset contains 9358 instances of hourly averaged responses from an array of 5 metal oxide chemical sensors embedded in an Air Quality Chemical Multisensor Device. The device was located on the field in a significantly polluted area, at road level,within an Italian city. Data were recorded from March 2004 to February 2005 (one year)representing the longest freely available recordings of on field deployed air quality chemical sensor devices responses. Ground Truth hourly averaged concentrations for CO, Non Metanic Hydrocarbons, Benzene, Total Nitrogen Oxides (NOx) and Nitrogen Dioxide (NO2) and were provided by a co-located reference certified analyzer. Evidences of cross-sensitivities as well as both concept and sensor drifts are present as described in De Vito et al., Sens. And Act. B, Vol. 129,2,2008 (citation required) eventually affecting sensors concentration estimation capabilities. Missing values are tagged with -200 value.

This dataset can be used exclusively for research purposes. Commercial purposes are fully excluded.

### Attribute Information:

0 Date (DD/MM/YYYY)

1 Time (HH.MM.SS)

2 True hourly averaged concentration CO in mg/m^3 (reference analyzer)

3 PT08.S1 (tin oxide) hourly averaged sensor response (nominally CO targeted)

4 True hourly averaged overall Non Metanic HydroCarbons concentration in microg/m^3 (reference analyzer)

5 True hourly averaged Benzene concentration in microg/m^3 (reference analyzer)

6 PT08.S2 (titania) hourly averaged sensor response (nominally NMHC targeted)

7 True hourly averaged NOx concentration in ppb (reference analyzer)

8 PT08.S3 (tungsten oxide) hourly averaged sensor response (nominally NOx targeted)

9 True hourly averaged NO2 concentration in microg/m^3 (reference analyzer)

10 PT08.S4 (tungsten oxide) hourly averaged sensor response (nominally NO2 targeted)

11 PT08.S5 (indium oxide) hourly averaged sensor response (nominally O3 targeted)

12 Temperature in °C

13 Relative Humidity (%)

14 AH Absolute Humidity

## Procesos de análisis a considerar.
### 1. Series de tiempo:
Las primeras dos columnas, correspondientes a `Date` y a `Time`, nos entregan una dimensión temporal que dota a la base de datos de una estructura de orden y condicionan los datos a la información del dato anterior. Para este contexto llamaremos como _t_ al índice temporal, y a la observación en ese tiempo como _obs(t)_. En ocaciones, estaremos interesados en tiempos anteriores al punto objetivo a estimar, llamados _lag times_. Denotaremos a los tiempos pasados como traslaciones del tiempo objetivo, por ejemplo, el momento antecesor al tiempo _t_ se denotará como _t-1_, y su observación en ese momento como _obs(t-1)_. De la misma forma para los tiempos futuros, por ejemplo, al tiempo sucesor de _t_ lo llamaremos _t+1_, y a su observación _obs(t+1)_. Si necesitamos referirnos a saltos más largos de tiempo seguiremos la misma lógica:
  - `t+n` para referirnos a _n_ pasos en el futuro.
  - `t` para el tiempo actual.
  - `t-n` para referirnos a _n_ pasos en el apsado.

