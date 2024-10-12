# Predicción del naufragio del Titanic

# Titanic Challenge

Welcome to the **Titanic Prediction Challenge**! This project aims to develop a model that predicts whether a passenger will survive the Titanic Disaster.

## 📋 Índice

- [📖 Descripción](#📖-descripción)
- [📋 Índice](#📋-índice)
- [👤 Instrucciones para el usuario](#👤-instrucciones-para-el-usuario)
- [⚙️ Instalación](#⚙️-instalación)
- [📊 Análisis de los datos](#📊-análisis-de-los-datos)
- [🔧 Ingeniería de variables](#🔧-ingeniería-de-variables)
- [🤖 Entrenamiento del modelo](#🤖-entrenamiento-del-modelo)
- [🏆 Resultados y conclusión](#🏆-resultados-y-conclusión)

## 📖 Descripción

## 👤 Instrucciones para el usuario

Para poder descargar los datos desde Kaggle, necesitas una API key de Kaggle.
1. Ve a tu cuenta de Kaggle (https://www.kaggle.com/account)
2. En la sección API, haz clic en "Create New API Token". Esto descargará el archivo `kaggle.json`.
3. Coloca el archivo `kaggle.json` en la carpeta `~/.kaggle/` (en sistemas UNIX como Linux/Mac) o en `C:\Users\TU_USUARIO\.kaggle\` (en Windows).
4. Asegúrate de que la carpeta tenga los permisos adecuados (`chmod 600` en UNIX).

Alternativa manual: navega a la URL https://www.kaggle.com/competitions/titanic, descarga y descomprime los archivos en una carpeta `/kaggle_data` en la misma ubicación que el notebook.

## ⚙️ Instalación

Para instalar las dependencias necesarias, ejecuta el siguiente comando:

```sh
pip install -r requirements/requirements.txt
```

## 📊 Análisis de los datos

Comenzaremos el trabajo con un breve análisis. Leeremos los datos, mostraremos el tabular, describiremos las columnas e imprimiremos una fila de cada tabla para tener una idea inicial.

## 🔧 Ingeniería de variables

En esta sección, realizaremos la ingeniería de variables necesaria para preparar los datos para el modelo de aprendizaje automático.

### Ticket

En este apartado trataremos los tickets, puede ser interesante dividir en 2 partes el ticket:

1) El prefijo, que reagruparemos puesto que parece que hay varias cadenas de caracteres que se refieren a lo mismo.

2) El número de ticket.

### Name

Trataremos la columna Name, uno puede pensar que una columna Name nunca es útil ya que actúa de forma similar al identificador. Pero en este dataset, debido a la época, todos los nombres tienen su respectivo título Mr., Mrs., Miss., etc.

Este título puede reforzar la información sobre el sexo y la edad (que además tiene algunos nulos), o el rol que desempeña esa persona dentro de la tripulación.

### Cabin

Cubriremos los nulos y haremos split de la cabina en número y letra.

### AgeCategory

Crearemos categorías de edad y una columna para informar qué pasajeros no informaron de su edad.

## 🤖 Entrenamiento del modelo

Entrenaremos varios modelos de aprendizaje automático y seleccionaremos el mejor basado en métricas de rendimiento.

### Versión 1 :

Modelo básico con RandomForest y todas las variables transformadas a dummies. Punto de partida.

### Versión 2 :

Regresión Logística tras transformar todas las variables a numéricas.

Llegamos a la conclusión de que hasta despues de hacer GridSearch, se producía Overfitting, así que nos decantamos por cambiar de modelo.

### Versión 3:

Volvemos a usar RandomForest, pero esta vez profundizando un poco más. Vamos a escoger las variables que más relación tengan con el target, convertir las variables a numéricas y GridSearch para llegar a una solución.

## 🏆 Resultados y conclusión

Presentaremos los resultados obtenidos y las conclusiones derivadas del análisis y modelado de los datos.

Es un modelo en el que se produce overfitting con facilidad. En las validaciones cruzadas sobre el conjunto de train suelen salir mejores predicciones que al aplicar la submission al test.

Intentamos evitar esto con GridSearch.

Uno de los aciertos de este trabajo para mí ha sido extraer el título que precede al nombre y almacenarlo como una variable categorica. (Mr, Miss, Mrs, Don, Donna, Captain, etc.)
Ha sido una de las variables que el modelo ha clasificado con mayor importancia, despues del sexo y la edad.

Alcanzamos el puesto 1200 de la clasificación, sobre 14620 participantes, en el concurso de Kaggle con una predicción sobre el conjunto de test de 0.78947, no está mal teniendo en cuenta que al ser un conjunto de datos relativamente pequeño, hay algunas participaciones que se han hecho con métodos que quedan fuera del marco del Machine Learning y los modelos de predicción.

Ha sido un buen aprendizaje construir este modelo, y me ha servido para adquirir conocimientos sobre cómo tratar un conjunto de datos y crear un modelo de clasificación. Tengo ganas de enfrentarme a problemas reales con mayores conjuntos de datos.

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Por favor, abre un issue o envía un pull request para contribuir a este proyecto.

## 📜 Licencia

Este proyecto está licenciado bajo la Licencia MIT. Consulta el archivo LICENSE para más detalles.

