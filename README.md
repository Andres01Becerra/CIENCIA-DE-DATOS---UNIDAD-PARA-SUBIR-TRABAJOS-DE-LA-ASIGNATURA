# Trabajos-de-Ciencia-de-Datos
Este espacio está diseñado para centralizar, organizar y compartir trabajos, proyectos y análisis relacionados con la materia ciencia de datos.
from google.colab import files
import pandas as pd

# Subir archivo manualmente desde la computadora
uploaded = files.upload()

# Obtener el nombre del archivo
file_name = list(uploaded.keys())[0]

# Cargar el archivo en un DataFrame
df = pd.read_excel(file_name)

# Ver las primeras 5 filas
df.head()
     
Upload widget is only available when the cell has been executed in the current browser session. Please rerun this cell to enable.
Saving Datos Prueba.xlsx to Datos Prueba.xlsx
ID	Edad	Salario	Departamento	Puntaje_Desempeño
0	1	56	28392	RRHH	4.744619
1	2	46	50535	Marketing	3.784119
2	3	32	98603	Marketing	3.280245
3	4	25	72256	Ventas	1.388706
4	5	38	55222	Ventas	3.460029

df.info()
df.describe()
df.head(100)
     
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 100 entries, 0 to 99
Data columns (total 5 columns):
 #   Column             Non-Null Count  Dtype  
---  ------             --------------  -----  
 0   ID                 100 non-null    int64  
 1   Edad               100 non-null    int64  
 2   Salario            100 non-null    int64  
 3   Departamento       100 non-null    object 
 4   Puntaje_Desempeño  100 non-null    float64
dtypes: float64(1), int64(3), object(1)
memory usage: 4.0+ KB
ID	Edad	Salario	Departamento	Puntaje_Desempeño
0	1	56	28392	RRHH	4.744619
1	2	46	50535	Marketing	3.784119
2	3	32	98603	Marketing	3.280245
3	4	25	72256	Ventas	1.388706
4	5	38	55222	Ventas	3.460029
...	...	...	...	...	...
95	96	59	69811	Ventas	4.425959
96	97	56	22811	RRHH	3.634775
97	98	58	76250	IT	1.651738
98	99	45	92082	Ventas	1.282275
99	100	24	54754	IT	3.569677
100 rows × 5 columns


import matplotlib.pyplot as plt
import seaborn as sns

plt.figure(figsize=(10, 5))
sns.histplot(df['Edad'], bins=20, kde=True)
plt.title('Distribución de la Edad')
plt.xlabel('Edad')
plt.ylabel('Frecuencia')
plt.savefig("histograma_edad.png")
plt.show()

plt.figure(figsize=(10, 5))
sns.countplot(y=df['Departamento'], order=df['Departamento'].value_counts().index)
plt.title('Distribución de Empleados por Departamento')
plt.xlabel('Cantidad de Empleados')
plt.ylabel('Departamento')
plt.savefig("barras_departamento.png")
plt.show()

plt.figure(figsize=(10, 5))
sns.scatterplot(x=df['Salario'], y=df['Puntaje_Desempeño'])
plt.title('Relación entre Salario y Puntaje de Desempeño')
plt.xlabel('Salario ($)')
plt.ylabel('Puntaje de Desempeño')
plt.savefig("dispersion_salario_puntaje.png")
plt.show()
     




df.to_csv("datos_procesados.csv", index=False)
from google.colab import files
files.download("datos_procesados.csv")
files.download("histograma_edad.png")
files.download("barras_departamento.png")
files.download("dispersion_salario_puntaje.png")
