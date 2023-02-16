
![Agregar un título](https://user-images.githubusercontent.com/117865649/219290455-d8290e3f-e321-4ca7-b42b-ea8286c6e986.png)
#Problema
Desarrollar un programa en C que permita jugar el juego “sopa de letras”. Requisitos de la aplicación:

Deberá generar una matriz de caracteres de nxn (10 <= n <= 35)
Deberá permitir el ingreso de k palabras por teclado ( [n/2]<= k <= [2*n] ), de tamaño igual o menor a n, las cuales se ubicarán en la matriz en una posición al azar en una fila o columna. Las palabras deben ser de tamaño mayor o igual que 2. Las palabras pueden estar escritas de izquierda a derecha, de derecha a izquierda, de arriba hacia abajo o de abajo hacia arriba. La orientación de la palabra también debe ser generada en forma aleatoria.
Luego del ingreso de las k palabras a la matriz, deberá llenar el resto de la matriz con caracteres del alfabeto en forma aleatoria.
Las k palabras ingresadas como los caracteres aleatorios debes estar en mayúscula, si el usuario ingresa las palabras en minúsculas el programa deberá transformarlas a mayúsculas.
Juego
El usuario deberá encontrar las palabras. Por cada palabra encontrada, el jugador deberá digitarla y su programa deberá verificar que efectivamente la palabra se encuentra presente, mostrando en pantalla la coordenada (celda y columna) en donde comienza la palabra y su orientación.
Su programa deberá permitir un máximo de 3 errores en total
El programa debe registrar y mostrar por pantalla el tiempo que demora el usuario en encontrar las k palabras ingresadas
