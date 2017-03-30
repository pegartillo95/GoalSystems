Respuestas
========

Conocimiento C++
-------------
1.  Al hacer el incremento 'b' valdrá cuatro. Ademas al ser un pre-incremento este se hace antes de comparar la variable con '4' por ello esa comparacion devolverá true.
2. Los templates en C++ son la base de la programación genérica. Este tipo de programacion nos permite escribir una clase o una funcion de manera que despues pueda ser utilizada con cualquier tipo. Un ejemplo sería escribir una estructura de datos como un stack con templates, de manera que despues dentro de dicho stack podemos guardar datos de cualquier tipo.
3. El primero es se trata de un puntero a una constante mientras el segundo es un puntero constante.
    * El puntero a una constante permite variar el puntero, es decir a que variable apunta pero no permite variar el valor de la variable a la que apunta.
    * El puntero constante es el caso opuesto. No permite variar a que variable apunta dicho puntero pero si que permite modificar el valor de dicha variable.
4. El mayor problema o mejor dicho limitación de retornar por copia es que solo puedes devolver un solo valor por cada función mientras que si devuelves por referencia puedes devolver tantos valores como quieras.
La ventaja del operador += es que te permite simplificar aquellos casos en los que la variable a la cual le asignas el valor y uno de los sumando coinciden. Se trata de un incremento (al igual que el ++) pero que puede ser de mas de una unidad. El inconveniente frente a + es que simplemente vale para realizar incrementos sobre una variable, en realidad se trata de un atajo para un caso específico de la suma.

5. En primer lugar la funcion recibe como parametros dos punteros a constantes en este caso dos arrays de char(strings) lo cual nos permite asegurarnos de que los valores de dichos array una vez salgamos de la funcion no han sido modificados respeto a su valor antes de entrar.
Una vez dentro de la función lo primero mira cual de las dos strings tiene mayor longitud y guarda el valor de la mas larga en c.
El bucle for se encarga de recorrer ambas strings y comprobar si son iguales en todas sus posiciones. Si son iguales en todas ellas al salir del bucle devolverá cero y sabremos que en efecto son iguales. Pero si devuelve cualquier otro valor (que en este caso es la diferencia entre los valores de los arrays a y b en la primera posicion que es distinta) sabremos que las dos strings no son iguales.
El problema que le veo es que si uno de los arrays es mas largo que lo otro en el bucle vamos a acceder a posiciones de memoria que en realidad no pertenecen al array.
6. 
7. 
8. El código no es correcto, al ejecutarlo se produciría un error en esta linea 
     ```c++
   b.Set(1,2,3,4);
    ```
    Pues como la clase B que hereda de la clase A tiene un metodo que se llama Set también y ve que el numero de parametros no coincide no mira en la clase A si existen otros métodos Set con distinto número de parámetros. Es decir el método de la clase B oculta al de la clase A.
    La manera de solucionar este problema sería cambiando la definicion de la clase B por esta
    ```c++
    class B : public A {
    public:
        using A::Set;
        void Set( int ) { std::cout << "usando Set de B" << std::endl; }
    };
    ```
    Lo cual permitirá que la funcion definida en la clase A participe en la resolución del overload y no de error.
    

Programación C++
-------------
9. 
10. 
11. 

Programación SQL
-------------
12. Para el problema de tener varios empleados y cada uno de ellos puede tener varias viviendas (ciudad, calle, piso) se me ocurre esta solucion de tres tablas en SQL.
    ```sql
    CREATE TABLE Empleado (
        ID NUMERIC NOT NULL PRIMARY KEY,
        Nombre VARCHAR(100) NOT NULL,
        Apellido VARCHAR(100) NOT NULL,
        ViviendaHabit VARCHAR(100) NOT NULL REFERENCES Viviendas (IdVivienda)
        ON DELETE CASCADE
    );

    CREATE TABLE ViviendasPersona (
        IdPersona NUMERIC NOT NULL REFERENCES Empleado (ID),
        Vivienda VARCHAR(100) NOT NULL REFERENCES Viviendas (IdVivienda)
    );

    CREATE TABLE Viviendas (
        IdVivienda VARCHAR(100) PRIMARY KEY,
        Ciudad VARCHAR(100),
        Calle VARCHAR(100),
        Piso VARCHAR(100)
    );
    ```
13. 
14. 
15. 
