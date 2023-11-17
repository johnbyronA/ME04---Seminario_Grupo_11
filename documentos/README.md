## Especialización en analítica y ciencia de datos 2023 - Cohorte VI

### ME04 Seminario - John Byron Alzate, Jorge Genes Padilla


### Generalidades del proyecto a realizar

El presente repositorio contiene la data y el análisis pertinente al alcance establecido para la entrega #4 de la asignatura Seminario de la Especialización en Analítica y Ciencia de Datos 2023 - Cohorte VI - Universidad de Antioquia.

El repositorio actual es de uso público, por lo tanto, cualquier aporte, inquietud u observación será muy bien recibida y atendida por los autores a través de pull requests o comentarios generales.

### Insumos del proyecto

El presente proyecto contiene los siguientes archivos de acuerdo con los lineamientos estipulados en la rúbrica:

1. bd_entrega_4.csv: Dataset original encontrado en la página web de MEData; sin transformar, contiene mas de un millón de filas de registros y mas de 60 columnas. Debido a su peso no puede ser cargado en el presente repositorio, pero puede descargarse a través del siguiente enlace: https://drive.google.com/file/d/1yEoAMXfNiC8sVAktT77Ryumm-_yYcXcP/view?usp=drive_link
2. Entrega_4_seminario_DEF.ipynb: Archivo con el código utilizado para el análisis estadístico y transformación del dataset anterior; Se encuentra en el repositorio actual.
3. ME04 - Avance Monografía.pdf: Rúbrica del Momento evaluativo #4 de la asignatura Seminario, Especialización en analítica y ciencia de datos 2023 - Cohorte VI; Se encuentra en el repositorio actual.
4. bd_entrega_4_archivo_salida: Archivo que contiene el dataset transformado, despues de aplicarsele técnicas de categorización y clasificación de variables. Se obtiene durante la ejecución del código y se encuentra en el repositorio actual.
5. README.md: Archivo presente; Se encuentra en el repositorio actual.
6. G11-ME04-JohnAlzate-JorgeGenes.docx: Documento que contiene todo el analisis realizado para el momento evaluativo #4 de la asignatura seminario; Se encuentra en el repositorio actual.

### Origen de los datos

El nombre de la base de datos es "Base de Datos SISBEN 2017", la cual proviene de la página web de MEData, repositorio de datos abiertos generados y publicados por las diferentes dependencias de la Alcaldía de Medellín.

El enlace directo al dataset es el siguiente: http://medata.gov.co/dataset/base-de-datos-sisben-2017

### Pasos para la ejecución del código

#### INSTRUCCIONES:

1.	Ingresar a https://github.com/johnbyronA/ME04---Seminario_Grupo_11
2.	Descargar los archivos bd_entrega_4.csv y Entrega_4_seminario_DEF.ipynb a la máquina local.
3.	Ingresar a https://colab.research.google.com/
4.	Dar clic en la opción "Subir", posteriormente dar clic en la opción "Explorar".
5.	Ubicar el archivo "Entrega_4_seminario_DEF.ipynb" dentro de la máquina local.
6.	Dar clic en la opción "Abrir" que se encargará de cargar el archivo al servicio de Google Colab en la nube.
7.	Dar clic al icono de la carpeta en la barra lateral izquierda de la pantalla.
8.	Dar clic al botón con el icono de la carpeta con una flecha apuntando hacia arriba (Subir al almacenamiento de sesión).
9.	Ubicar el archivo "bd_entrega_4.csv" dentro del PC local, darle clic a la opción "Abrir".
10.	Esperar a que el archivo cargue completamente.
11.	Ejecutar todo el código presionando la combinación de teclas CTRL + F9
12.	Esperar unos minutos a que todas las líneas sean ejecutadas para ver los resultados de los comandos empleados.

## Contenido académico y análisis de datos

#### ESTADÍSTICA DESCRIPTIVA

A continuación se listan los pasos que fueron seguidos para la obtención de las métricas de estadística descriptiva de las variables del dataset:

1. Se realiza la conversión de la columna "FECHANTO" a formato de fecha y con base en ella, se calcula la edad de cada usuario en los registros.
2. Se categoriza la columna "EDAD" en rangos de edad especificos.
3. Se crea una variable 'Puntaje_Categorico' para categorizar la variable de salida 'PUNTAJE' 
4. Se elimina la columna 'Puntaje' y se eliminan los registros duplicados de todo el dataset.
5. Se cambian las columnas con comportamiento categórico a formato 'object'
6. Se establecer estilos de Seaborn y se determinan el número de filas y columnas para  crear los subgráficos de las variables categóricas
7. Se establecen las variables numéricas del dataset y se verifica que sean de tipo numéricas.
8. Se realiza el conteo del número de registros de la variable 'Puntaje_Categorico' y se procede a graficarlos en una gráfica de torta.
9. Se disminuye el número de registros del dataset a una muestra aleatoria de 100000 (Cien mil) registros con una semilla número 42, para que en cada ejecución, siempre sean los mismos registros.


#### MODELOS DE ML (MACHINE LEARNING)

Para el alcance actual de la entrega #4, se tuvieron en cuenta tan solo dos modelos de ML, el modelo RandomForest y el modelo de Regresion Logística. Estos fueron empleados en un análisis temprano de la solución para permitir al lector evidenciar el enfoque que será empleado en la futura monografía en un alcance posterior de la especialización.

Tales modelos tienen las siguientes características respectivamente:

1. Se realiza el escalado de características mediante funcion StandardScaler() de la libreria sklearn, lo anterior se realiza debido a que el escalado garantiza que ninguna característica domine sobre otra en términos de magnitud.

2. El entrenamiento de todos los modelos de ML fue realizado con base a un test_size del 30% y un train size del 70% de los datos:


```
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)
```

3. Uso de la caracteristica predict de la libreria sklearn, para evaluar las funciones y caracteristicas de los modelos RandomForest y Logistic Regression: 

```
y_pred = lr.predict(X_test_scaled)
y_pred = rf_classifier.predict(X_test_scaled)
```

4. Uso de la caracteristica score de la libreria sklearn, para evaluar la precision de los datos de entrenamiento y de prueba de los modelos RandomForest y Logistic Regression: 

```
tr_accuracy = rf_classifier.score(X_train_scaled, y_train)

ts_accuracy = accuracy_score(y_test, y_pred)
```

5. Uso de matrices de confusión mediante libreria sklearn, para observar gráficamente y de forma ordenada en tabla, las métricas de desempeño que se usaran para evaluar la efectividad y precisión de la prediccion de los modelos de ML propuestos (Precision, recall, f1-score) :


               precision    recall  f1-score   support

           0       0.77      0.86      0.81     16810
           1       0.79      0.68      0.73     13190

donde 0 y 1 son los valores clasificatorios de la variable "Puntaje_categorico"

## Conclusiones:

El alcance del presente documento README.md corresponde al ME04 para la asignatura seminario de la Especialización en analítica y ciencia de datos 2023 - Cohorte VI. Para la entrega de la monografía final se tendra en cuenta un analisis mas amplio, empleando mayor variedad de modelos de ML y diferentes técnicas visuales para evidenciar que modelo clasificatorio es quien obtiene mejores resultados, también se espera aplicar conocimientos adquiridos en asignaturas futuras, para asi mejorar la calidad del análisis y la claridad del mismo.

Cualquier recomendación, corrección u observación, son bienvenidas.