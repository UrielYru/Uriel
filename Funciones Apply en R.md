- Class: funciones apply,lapply, sapply, rep
  Course: programacion-estadistica-r
  Lesson: Funciones apply
  Author: Ismael Fernández
  Type: Standard
  Organization: Universidad Nacional Autónoma de México
  Version: 2.2.21

- Class: text
  Output: "En esta lección aprenderás a utilizar a la familia de funciones
  *apply()."

- Class: text
  Output: "Cuando te encuentras procesando información, una operación común es
  la de aplicar una función a un conjunto de elementos y regresar un nuevo
  conjunto de elementos."

- Class: text
  Output: "La funciones *apply() que se encuentran en el paquete base de R,
  actúan de esta manera sobre diferentes estructuras de datos, aplican una
  función con uno o varios argumentos y regresan otra estructura de datos."

- Class: text
  Output: "La primera función que conocerás es la función apply(), la cual opera
  sobre arreglos."

- Class: cmd_question
  Output: 'Para conocer el uso de esta función ingresa help("apply") en la línea
  de comandos.'
  CorrectAnswer: help("apply")
  AnswerTests: any_of_exprs('help("apply")', '?apply', '?"apply"', 'help(apply)')

- Class: text
  Output: "X es un arreglo (puede ser una matriz si la dimensión del arreglo es
  2). MARGIN es una variable que define cómo la función es aplicada, cuando
  MARGIN=1 se aplica sobre los renglones, cuando MARGIN=2 trabaja sobre las
  columnas. FUN es la función que deseas aplicar y puede ser cualquier función
  de R, incluyendo funciones definidas por ti."

- Class: text
  Output: "Opcionalmente puedes especificar argumentos a FUN como argumentos
  adicionales (...)."

- Class: cmd_question
  Output: "Para ejemplificar cómo funciona crea un arreglo bidimensional
  (matriz) y guárdalo en la variable 'mi_matriz'. Ingresa mi_matriz <-
  matrix(data=1:16,nrow=4, ncol=4) en la línea de comandos."
  CorrectAnswer: mi_matriz <- matrix(data=1:16,nrow=4, ncol=4)
  AnswerTests: omnitest(correctExpr='mi_matriz <- matrix(data=1:16,nrow=4, ncol=4)')

- Class: cmd_question
  Output: 'Ahora ve su contenido.'
  CorrectAnswer: mi_matriz
  AnswerTests: any_of_exprs('mi_matriz', 'print(mi_matriz)')
  Hint: "Recuerda que para ver el contenido de una variable puedes usar la
  función print() o simplemente ingresar el nombre de la variable en la línea
  de comandos."

- Class: cmd_question
  Output: "Ahora imagina que deseas saber el mínimo valor presente en cada
  columna de 'mi_matriz'. Puedes usar la funcion min(), la cual regresa el
  mínimo de los valores que recibe como entrada; y así, al ingresar
  apply(X=mi_matriz, MARGIN=2, FUN=min) en la línea de comandos obtendrás los
  mínimos valores por columna. ¡Inténtalo!"
  CorrectAnswer: apply(mi_matriz, 2, min)
  AnswerTests: omnitest(correctExpr='apply(mi_matriz, 2, min)')

- Class: text
  Output: "Es importante notar que es necesario que MARGIN=2 para que la función
  min() sea aplicada sobre las columnas."

- Class: cmd_question
  Output: 'Ahora haz la misma operación, solo que sobre los renglones.'
  CorrectAnswer: apply(mi_matriz, 1, min)
  AnswerTests: omnitest(correctExpr='apply(mi_matriz, 1, min)')
  Hint: "Recuerda que debes cambiar MARGIN=1 para aplicar la función sobre
  renglones."

- Class: text
  Output: "Te preguntarás qué puedes hacer si deseas aplicar una función a una
  lista o un vector, ya que apply() solo opera sobre arreglos."

- Class: text
  Output: 'Pues bien, para aplicar una función a cada elemento de un vector o
  una lista y regresar una lista, puedes usar la función lapply().'

- Class: cmd_question
  Output: 'Para ejemplificar esto crea una lista, la cual contenga a las cadenas
  "Introducción", "a", "la", "Programación", "Estadística", "con", "R", en ese
  orden, y guarda la lista en la variable ‘mi_lista’.'
  CorrectAnswer: mi_lista <- list("Introducción", "a", "la", "Programación", "Estadística", "con", "R")
  AnswerTests: omnitest(correctExpr='mi_lista <- list("Introducción", "a", "la", "Programación", "Estadística", "con", "R")')
  Hint: "Recuerda que para crear una lista con ciertos elementos simplemente
  debes usar la función list() y pasarle como argumento los elementos que desees
  que contenga."

- Class: cmd_question
  Output: "Ahora ve el contenido de la variable 'mi_lista'."
  CorrectAnswer: mi_lista
  AnswerTests: any_of_exprs('mi_lista', 'print(mi_lista)')
  Hint: "Recuerda que para ver el contenido de una variable puedes usar la
  función print() o simplemente ingresar el nombre de la variable en la línea de
  comandos."

- Class: cmd_question
  Output: 'Aunque la función lapply() es muy parecida a la función apply(), es
  importante conocer la manera de usarla; esto lo puedes hacer conociendo sus
  argumentos. Ahora ve los argumentos de la función lapply().'
  CorrectAnswer: formals(lapply)
  AnswerTests: any_of_exprs('formals(lapply)', 'args(lapply)')
  Hint: 'Recuerda que para conocer los argumentos de una función basta con hacer
  uso de la función formals() o args() mandando el nombre de la función de la
  que deseas conocer los argumentos.'

- Class: text
  Output: "Como podrás notar el uso de lapply() es más simple que el de apply,
  puesto que no hace uso del argumento MARGIN."

- Class: cmd_question
  Output: 'Ahora ve un simple ejemplo de cómo usar lapply. Ingresa mayusculas <-
  lapply(mi_lista, toupper) en la línea de comandos.'
  CorrectAnswer: mayusculas <- lapply(mi_lista, toupper)
  AnswerTests: omnitest(correctExpr='mayusculas <- lapply(mi_lista, toupper)')

- Class: cmd_question
  Output: "Ahora ve el contenido de 'mayusculas'."
  CorrectAnswer: mayusculas
  AnswerTests: any_of_exprs('mayusculas', 'print(mayusculas)')
  Hint: "Recuerda que para ver el contenido de una variable puedes usar la
  función print() o simplemente ingresar el nombre de la variable en la línea de
  comandos."

- Class: text
  Output: "Como recordarás, toupper() regresa la cadena que reciba como entrada
  en mayúsculas. Así que lapply simplemente regresa una lista que contiene el
  resultado de aplicar la función toupper() a cada elemento de 'mi_lista'."

- Class: cmd_question
  Output: "Para verificar que lapply efectivamente regresa una lista ingresa
  class(mayusculas)."
  CorrectAnswer: class(mayusculas)
  AnswerTests: omnitest(correctExpr='class(mayusculas)')

- Class: mult_question
  Output: 'Si ahora ingresas lapply(c("Introduccion", "a", "la", "Programacion",
  "Estadistica", "con", "R"), toupper) en la línea de comandos, ¿qué crees que
  ocurra?'
  CorrectAnswer: Que te regrese una lista que contenga las cadenas "INTRODUCCION", "A", "LA", "PROGRAMACION", "ESTADISTICA", "CON", "R"
  AnswerChoices: Que te regrese una lista que contenga las cadenas "INTRODUCCION", "A", "LA", "PROGRAMACION", "ESTADISTICA", "CON", "R"; Que te mande error; Que te regrese un vector que contenga las cadenas "INTRODUCCION", "A", "LA", "PROGRAMACION", "ESTADISTICA", "CON", "R"
  AnswerTests: omnitest(correctVal='Que te regrese una lista que contenga las cadenas "INTRODUCCION", "A", "LA", "PROGRAMACION", "ESTADISTICA", "CON", "R"')

- Class: text
  Output: 'Te regresará una lista que contenga a las cadenas "INTRODUCCION",
  "A", "LA", "PROGRAMACION", "ESTADISTICA", "CON", "R" pues si recuerdas la
  función lapply() opera sobre listas y vectores y SIEMPRE regresa una lista;
  es fácil que recuerdes esto si piensas que lista + apply = lapply.'

- Class: figure
  Output: 'A partir de ahora trabajarás con el archivo
  ASA_estadisticasPasajeros(3).csv, el cual contiene datos estadísticos del año
  2015 de pasajeros en servicio nacional e internacional de la Red Aeropuertos y
  Servicios Auxiliares de México. Con suerte, el archivo se mostrará en algún
  editor. De lo contrario, búscalo en el subdirectorio swirl_temp, de tu
  directorio de trabajo y velo en una aplicación separada.'
  Figure: showASA_estadisticasPasajeros(3).R
  FigureType: new

- Class: text
  Output: 'Como podrás notar el primer renglón del archivo contiene los nombres
  de las columnas. Anio mes son representados por una cadena que contiene año y
  mes pegados sin espacios; Código IATA se refiere a la sigla utilizada por
  IATA(International Air Transport Association) para identificar al aeropuerto;
  Descripción contiene la ciudad donde se encuentra dicho aeropuerto; Estado,
  como su nombre lo indica, contiene el nombre del estado donde se encuentra
  dicho aeropuerto; Pasajeros nacionales se refiere al número de pasajeros
  mexicanos que hicieron uso del aeropuerto; y Pasajeros internacionales se
  refiere al número de pasajeros extranjeros que hicieron uso del aeropuerto.'

- Class: cmd_question
  Output: 'Ahora importa el archivo ASA_estadisticasPasajeros(3).csv usando
  alguna función read.*() y guárdalo en la variable ‘asa_datos’. Recuerda que se
  encuentra en tu directorio de trabajo, en la carpeta swirl_temp, por lo que la
  ruta del archivo es "swirl_temp/ASA_estadisticasPasajeros(3).csv"'
  CorrectAnswer: asa_datos <- read.csv("swirl_temp/ASA_estadisticasPasajeros(3).csv")
  AnswerTests: any_of_exprs('asa_datos <- read.csv("swirl_temp/ASA_estadisticasPasajeros(3).csv")',  'read.table("swirl_temp/ASA_estadisticasPasajeros(3).csv",header=TRUE, sep=",", fileEncoding = "latin1")', 'read.table("swirl_temp/ASA_estadisticasPasajeros(3).csv",header=TRUE, sep=",")', 'asa_datos <- read.csv("swirl_temp/ASA_estadisticasPasajeros(3).csv", header=TRUE)', 'asa_datos <- read.csv("swirl_temp/ASA_estadisticasPasajeros(3).csv", header=TRUE, fileEncoding = "latin1")', 'asa_datos<-read.csv("swirl_temp/ASA_estadisticasPasajeros(3).csv", header =TRUE, sep ="," )')
  Hint: "Recuerda que para leer archivos separados por comas se usa la función
  read.csv(), y recuerda guardar el contenido en la variable asa_datos."

- Class: cmd_question
  Output: 'Ahora ve lo que contiene ‘asa_datos’. Para hacer esto usarás la
  función View(). Si te encuentras en Rstudio simplemente puedes presionar el
  nombre de tu variable asa_datos en el apartado Entorno ("Environment") y se
  mostrará su contenido. Presiona la variable asa_datos en Rstudio o ingresa en
  la línea de comando: View(asa_datos).'
  CorrectAnswer: View(asa_datos)
  AnswerTests: omnitest(correctExpr='View(asa_datos)')

- Class: text
  Output: "Como recordarás la familia de funciones read.*() te regresan un data
  frame."

- Class: text
  Output: "Los data frames no son más que una lista de vectores, así que puedes
  usar la función lapply() con ellos."

- Class: text
  Output: "Es importante que cuando trabajes con datos sepas un poco más de
  ellos."

- Class: cmd_question
  Output: "Si deseas saber el tipo de variables que contiene cada columna del
  data frame 'asa_datos' basta con escribir lapply(asa_datos, class). Ingresa
  lapply(asa_datos, class) en la línea de comandos."
  CorrectAnswer: lapply(asa_datos, class)
  AnswerTests: omnitest(correctExpr='lapply(asa_datos, class)')

- Class: text
  Output: 'Como podrás notar, el data frame contiene dos tipos de datos:
  enteros (Anio.mes, Pasajeros.nacionales y Pasajeros.internacionales) y
  factores (Codigo.IATA, Descripcion y Estado).'

- Class: text
  Output: 'Como recordarás los factores son una colección ordenada de elementos.
  Son usados en R para representar valores categóricos. Si haces un poco de
  memoria recordarás que los valores que un factor puede tomar se llaman niveles
  ("levels").'

- Class: text
  Output: 'A la hora de trabajar con factores es importante que conozcas los
  niveles que los datos pueden tomar.'

- Class: cmd_question
  Output: 'Si deseas conocer los niveles que las columnas del data frame pueden
  tomar, los puedes conocer al imprimir dicha columna. Por ejemplo,
  ingresa asa_datos$Descripcion en la línea de comandos para conocer las
  ciudades que contienen aeropuertos pertenecientes a la Red Aeropuertos y
  Servicios Auxiliares de México.'
  CorrectAnswer: asa_datos$Descripcion
  AnswerTests: omnitest(correctExpr='asa_datos$Descripcion')

- Class: text
  Output: 'Como podrás notar esto presentó todos los valores de la columna
  Descripcion aun estando repetidos. Al final se muestran todos los niveles en
  donde dice "Levels:" pero al ser muchos R mostró algunos y los demás los
  omitió usando "...".'

- Class: cmd_question
  Output: 'Una manera de poder ver todos los niveles aun cuando sean muchos es
  usando la función unique(). La función unique() elimina duplicados. Ingresa
  unique(asa_datos$Descripcion) en la línea de comandos.'
  CorrectAnswer: unique(asa_datos$Descripcion)
  AnswerTests: omnitest(correctExpr='unique(asa_datos$Descripcion)')

- Class: text
  Output: "Ahora ya conoces las ciudades con aeropuertos pertenecientes a la red
  ASA."

- Class: cmd_question
  Output: 'Repite el proceso pero ahora para conocer los valores de la columna
  Estado.'
  CorrectAnswer: unique(asa_datos$Estado)
  AnswerTests: omnitest(correctExpr='unique(asa_datos$Estado)')

- Class: cmd_question
  Output: 'Ahora deseas saber el número total de pasajeros nacionales que
  viajaron en alguno de los aeropuertos pertenecientes a la red ASA. Para hacer
  esto simplemente puedes sumar todos los elementos de la columna de
  Pasajeros.nacionales. Ingresa sum(asa_datos$Pasajeros.nacionales) en la línea
  de comandos.'
  CorrectAnswer: sum(asa_datos$Pasajeros.nacionales)
  AnswerTests: omnitest(correctExpr='sum(asa_datos$Pasajeros.nacionales)')

- Class: text
  Output: 'La función sum() regresa la suma de todos los elementos que recibe
  como argumentos.'

- Class: text
  Output: 'Ahora deseas obtener el número total de pasajeros internacionales.'

- Class: text
  Output: 'Podrías repetir la operación que hiciste para obtener el número total
  de pasajeros nacionales...'

- Class: text
  Output: 'O podrías usar la función lapply() y automatizar la operación para
  obtener el número total de ambos pasajeros.'

- Class: cmd_question
  Output: 'Primero crea un subconjunto de asas_datos, ingresa asa_pasajeros <-
  asa_datos[,c("Pasajeros.nacionales", "Pasajeros.internacionales")] en la línea
  de comandos. Con esto obtendrás las columnas de pasajeros.'
  CorrectAnswer: asa_pasajeros <- asa_datos[,c("Pasajeros.nacionales", "Pasajeros.internacionales")]
  AnswerTests: omnitest(correctExpr='asa_pasajeros <- asa_datos[,c("Pasajeros.nacionales", "Pasajeros.internacionales")]')

- Class: cmd_question
  Output: 'Ahora ve lo que contiene ‘asa_pasajeros’. Para hacer esto usarás la
  función View(). Si te encuentras en Rstudio simplemente puedes presionar el
  nombre de la variable asa_pasajeros en el apartado Entorno ("Environment") y
  se mostrará su contenido. Presiona la variable asa_pasajeros en Rstudio o
  ingresa View(asa_pasajeros) en la línea de comandos.'
  CorrectAnswer: View(asa_pasajeros)
  AnswerTests: omnitest(correctExpr='View(asa_pasajeros)')

- Class: cmd_question
  Output: 'Y ahora usa la función lapply() para obtener el número total de
  pasajeros de ambas columna. Ingresa lapply(asa_pasajeros, sum) en la línea de
  comandos.'
  CorrectAnswer: lapply(asa_pasajeros, sum)
  AnswerTests: omnitest(correctExpr='lapply(asa_pasajeros, sum)')

- Class: text
  Output: 'Esto te dice que se registraron un total de 2 291 419 pasajeros
  nacionales y 176 741 pasajeros internacionales.'

- Class: text
  Output: 'Como recordarás, las listas son útiles para guardar objetos de
  múltiples clases. Pero en este caso el resultado de aplicar sum() fue un
  entero por columna; podrías guardar el resultado en alguna otra estructura.'

- Class: text
  Output: 'sapply() te permite simplificar este proceso; sapply funciona como
  lapply(), pero intenta simplificar la salida a la estructura de datos más
  elemental que sea posible. De ahí su nombre simple + apply = sapply.'

- Class: cmd_question
  Output: "Ahora usa sapply() para obtener el número total de pasajeros
  nacionales e internacionales de la misma manera que lo hiciste con lapply() y
  guarda el resultado en la variable 'total_pasajeros'."
  CorrectAnswer: total_pasajeros <- sapply(asa_pasajeros, sum)
  AnswerTests: omnitest(correctExpr='total_pasajeros <- sapply(asa_pasajeros, sum)')
  Hint: 'Usa sapply() para obtener el número total de pasajeros nacionales e
  internacionales. Si deseas ver el uso de sapply siéntete libre de ingresar
  ?sapply en la línea de comandos.'

- Class: cmd_question
  Output: "Ahora ve el contenido de 'total_pasajeros'."
  CorrectAnswer: total_pasajeros
  AnswerTests: any_of_exprs('total_pasajeros', 'print(total_pasajeros)')
  Hint: "Recuerda que para ver el contenido de una variable puedes usar la
  función print() o simplemente ingresar el nombre de la variable en la línea de comandos."

- Class: text
  Output: "Como notarás 'total_pasajeros' no es una lista; esto se debe a que a
  sapply() simplificó el resultado a un vector de enteros."

- Class: text
  Output: 'En general, si el resultado de lapply() es una lista donde cada
  elemento es de longitud 1, sapply() regresará un vector. Si el resultado es
  una lista donde cada elemento es un vector de la misma longitud (> 1),
  sapply() regresará una matriz. Si sapply() no puede arreglárselas, entonces
  regresará una lista, lo cual no sería diferente al resultado de usar
  lapply().'

- Class: text
  Output: 'Algunas veces encontrarás que los datos proporcionados tienen una
  granularidad muy fina para el tipo de análisis que estás realizando. Por
  ejemplo supón que deseas saber el número total de pasajeros nacionales por
  estado. Para encontrar ese número, tendrás que agrupar los aeropuertos por
  estado e ir sumando los números de pasajeros nacionales. Esta tarea puede
  volverse un poco conflictiva debido a que la información la tienes dividida
  por meses.'

- Class: cmd_question
  Output: 'Como recordarás, la columna Estados solo puede tomar los valores
  Sonora, Colima, Campeche, Quintana Roo, Tamaulipas, Baja California Sur,
  Veracruz, Puebla, Oaxaca, Nayarit, San Luis Potosí y Michoacán. Para ver
  cuántos registros tiene cada estado ingresa table(asa_datos$Estado) en la
  línea de comandos.'
  CorrectAnswer: table(asa_datos$Estado)
  AnswerTests: omnitest(correctExpr='table(asa_datos$Estado)')

- Class: text
  Output: 'Como te podrás dar cuenta cada estado tiene un número múltiplo de 12
  registros; esto se debe a que los registros por aeropuerto están divididos por
  mes.'

- Class: text
  Output: 'Pensando en que algunas veces tendrás la información con una
  granularidad muy fina para el tipo de análisis que deseas realizar, R
  proporciona la función tapply(), la cual divide datos en grupos, basados en
  valor de alguna variable y luego aplica la función especificada a los miembros
  de cada grupo.'

- Class: cmd_question
  Output: 'Ingresa tapply(asa_datos$Pasajeros.nacionales, asa_datos$Estado, sum)
  para obtener el número de pasajeros nacionales por estado.'
  CorrectAnswer: tapply(asa_datos$Pasajeros.nacionales, asa_datos$Estado, sum)
  AnswerTests: omnitest(correctExpr='tapply(asa_datos$Pasajeros.nacionales, asa_datos$Estado, sum)')

- Class: cmd_question
  Output: 'Ahora obtén el promedio o media de pasajeros nacionales que viajaron
  por mes en cada aeropuerto. Recuerda que para calcular la media puedes usar la
  función mean().'
  CorrectAnswer: tapply(asa_datos$Pasajeros.nacionales, asa_datos$Codigo.IATA, mean)
  AnswerTests: omnitest(correctExpr='tapply(asa_datos$Pasajeros.nacionales, asa_datos$Codigo.IATA, mean)')
  Hint: 'Ingresa tapply(asa_datos$Pasajeros.nacionales, asa_datos$Codigo.IATA,
  mean) en la línea de comandos para conocer la media de pasajeros nacionales
  que viajaron por mes en cada aeropuerto.'

- Class: mult_question
  Output: "Has concluido la lección. ¿Te gustaría que se le notificará a
  Coursera que has completado esta lección?"
  CorrectAnswer: NULL
  AnswerChoices: Si;No
  AnswerTests: coursera_on_demand()
  Hint: ""
