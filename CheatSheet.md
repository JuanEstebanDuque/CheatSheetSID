# Integrantes
* Juan Esteban Duque Taborda
* Sebastián Escobar Marín

# **Cheat Sheet**

Con este *Cheat Sheet* se buscar responder a las siguientes preguntas con el fin de tener los conceptos en un archivo fácil de acceder para cuando se requiera.

1. Describir la estructura general de un bloque PL/SQL (con un ejemplo).
2. ¿Cómo se hacen declaraciones de variables y constantes? Proponga ejemplos con distintos tipos de datos.
3. Explicar las instrucciones de control de PL/SQL, ilustre sus respuestas por medio de ejemplos.
4. Explique cómo se declaran y usan los procedimientos/funciones por medio de ejemplos.
5. ¿Qué es una excepción, cuáles son sus tipos y cómo se hace el manejo de excepciones?
6. ¿Qué son los cursores de SQL y cómo se declaran?  ilustre esto con un ejemplo.
7. ¿Qué son los triggers y para qué pueden ser utilizados?
8. Usando ejemplos, explique las diferencias entre los triggers  BEFORE, AFTER, e  INSTEAD OF.

_________________________________________________

## **Definición de PL/SQL**

Primeramente, debemos dejar en claro que es PL/SQL, sus diferencias a SQL y como funciona. Por consiguiente definiremos PL/SQL:

PL/SQL es un lenguaje de programación de bases de datos utilizado para crear aplicaciones y procesos almacenados dentro de una base de datos Oracle. PL/SQL se utiliza para escribir procedimientos almacenados, funciones, desencadenadores (triggers) y paquetes dentro de la base de datos. La sintaxis de PL/SQL se basa en SQL y proporciona características adicionales de programación, como control de flujo, estructuras de datos, manejo de excepciones, entre otras. PL/SQL se ejecuta dentro del motor de base de datos Oracle y, por lo tanto, es muy eficiente y escalable. PL/SQL tiene las siguientes diferencias a SQL:

1. SQL se utiliza principalmente para la manipulación de datos, mientras que PL/SQL se utiliza para la programación de aplicaciones y la automatización de procesos.
2. SQL es un lenguaje declarativo, mientras que PL/SQL es un lenguaje procedural. Esto significa que SQL se centra en lo que se quiere hacer con los datos, mientras que PL/SQL se centra en cómo se deben hacer las cosas.
3. SQL se utiliza principalmente para la consulta de datos, mientras que PL/SQL se utiliza para la manipulación de datos, la definición de funciones, procedimientos y paquetes.
4. SQL se puede utilizar en una variedad de sistemas de gestión de bases de datos, mientras que PL/SQL está diseñado específicamente para Oracle.

# **Respuesta a preguntas**

1. Describir la estructura general de un bloque PL/SQL (con un ejemplo).

## _1ra pregunta:_

Un bloque PL/SQL es una unidad básica de código que se compone de una serie de sentencias SQL y sentencias PL/SQL que se agrupan y ejecutan juntas. Los bloques PL/SQL se pueden utilizar para realizar una variedad de tareas como la manipulación de datos en una base de datos. Un ejemplo de su estructura general es el siguiente:

    *DECLARE*

      -- Declaración de variables
      var1 VARCHAR2(50);
      var2 NUMBER(10);
    
    *BEGIN*

      -- Código de ejecución del bloque
      SELECT nombre INTO var1 FROM tabla WHERE id = var2;
  
    -- Más código de ejecución
    *END;*
    /

Donde en la sesión **DECLARE** se declaran las variables a usar en el bloque. Y En la sesión **BEGIN** se escribe el código de ejecución del bloque.

________________________________________________

2. ¿Cómo se hacen declaraciones de variables y constantes? Proponga ejemplos con distintos tipos de datos.

## _2da pregunta:_

En PL/SQL se pueden hacer declaraciones de variables y constantes utilizando la palabra clave **DECLARE** como se explicó anteriormente. A continuación algunos ejemplos de declaración de variables y constantes.

_Declaración de variable numérica:_

    DECLARE
        cantidad NUMBER := 10;
    BEGIN
        -- código que utiliza la variable cantidad
    END;

_Declaración de una constante númerica:_

    DECLARE
        PI CONSTANT NUMBER := 3.141592653589793;
    BEGIN
         -- código que utiliza la constante PI
    END;

_Declaración de una variable de caracteres:_

    DECLARE
        nombre VARCHAR2(50) := 'Juan';
    BEGIN
        -- código que utiliza la variable nombre
    END;

_Declaración de una constante de caracteres:_

    DECLARE
        PI CONSTANT NUMBER := 3.141592653589793;
    BEGIN
        -- código que utiliza la constante PI
    END;

________________________________________________

3. Explicar las instrucciones de control de PL/SQL, ilustre sus respuestas por medio de ejemplos.

## _3ra pregunta:_

PL/SQL proporciona diversas instrucciones de control para manejar el flujo de ejecución del programa. Estas instrucciones permiten ejecutar diferentes bloques de código en función de una condición o repetir un bloque de código varias veces. A continuación se describen las principales instrucciones de control de PL/SQL:

_Instrucción **IF-THEN-ELSE**:_

Esta instrucción se utiliza para ejecutar un bloque de código si una condición es verdadera y otro bloque de código si la condición es falsa.

    IF (condición) THEN
        -- código a ejecutar si la condición es verdadera
    ELSE
        -- código a ejecutar si la condición es falsa
    END IF;

**Ejemplo**:

    DECLARE
        edad NUMBER(3) := 18;
    BEGIN
        IF (edad >= 18) THEN
            DBMS_OUTPUT.PUT_LINE('Eres mayor de edad');
        ELSE
            DBMS_OUTPUT.PUT_LINE('Eres menor de edad');
        END IF;
    END;

_Instrucción **CASE**:_

Esta instrucción se utiliza para ejecutar un bloque de código diferente en función del valor de una variable. 

    CASE variable
        WHEN valor1 THEN
            -- código a ejecutar si la variable es igual a valor1
        WHEN valor2 THEN
            -- código a ejecutar si la variable es igual a valor2
        ...
        ELSE
            -- código a ejecutar si la variable no coincide con ningún valor
    END CASE;

**Ejemplo**:

    DECLARE
        dia_semana VARCHAR2(10) := 'Martes';
    BEGIN
        CASE dia_semana
            WHEN 'Lunes' THEN
                DBMS_OUTPUT.PUT_LINE('Hoy es lunes');
            WHEN 'Martes' THEN
                DBMS_OUTPUT.PUT_LINE('Hoy es martes');
             WHEN 'Miércoles' THEN
                DBMS_OUTPUT.PUT_LINE('Hoy es miércoles');
            ELSE
                DBMS_OUTPUT.PUT_LINE('Hoy no es lunes, martes ni miércoles');
        END CASE;
    END;

_Instrucción **LOOP**:_

Esta instrucción se utiliza para repetir un bloque de código varias veces hasta que se cumpla una condición de salida. 

    LOOP
        -- código a ejecutar en cada iteración
        IF (condición_salida) THEN
            EXIT; -- salir del bucle
        END IF;
    END LOOP;

**Ejemplo**:

    DECLARE
        contador NUMBER(3) := 0;
    BEGIN
        LOOP
            contador := contador + 1;
            DBMS_OUTPUT.PUT_LINE('Contador = ' || contador);
            IF (contador >= 5) THEN
                EXIT; -- salir del bucle
            END IF;
        END LOOP;
    END;


_Instrucción **FOR LOOP**:_

Esta instrucción se utiliza para repetir un bloque de código un número determinado de veces.

    FOR variable IN valor_inicial..valor_final LOOP
        -- código a ejecutar en cada iteración
    END LOOP;

_______________________________________________

4. Explique cómo se declaran y usan los procedimientos/funciones por medio de ejemplos.

## _4ta pregunta:_

En PL/SQL, los procedimientos y funciones son bloques de código que se pueden llamar desde otros bloques de código o desde aplicaciones externas. A continuación un ejemplo de como se declara una función:

    CREATE OR REPLACE FUNCTION sum_numbers(num1 IN NUMBER, num2 IN NUMBER) RETURN NUMBER IS
        total NUMBER;
    BEGIN
        total := num1 + num2;
        RETURN total;
    END;

Donde se usa la palabra clave **CREATE OR REPLACE** seguida del _nombre del procedimiento_ o función, seguido de los _parámetros de entrada_ y las _declaraciones de variables_, seguido del _cuerpo del procedimiento_ o función.

Para llamar este bloque desde otra aplicación se realizaría de la siguiente forma:

    SELECT sum_numbers(10, 20) FROM _tabla elegida_;

_________________________________________________

5. ¿Qué es una excepción, cuáles son sus tipos y cómo se hace el manejo de excepciones?

## _5ta pregunta:_

En PL/SQL, una excepción es una condición anormal que puede ocurrir durante la ejecución de un bloque de código. Las excepciones se utilizan para manejar errores y situaciones inesperadas que pueden interrumpir el flujo normal de ejecución de un programa.

Existen dos tipos de excepciones en PL/SQL:

1. Excepciones predefinidas: Son las excepciones que ya están definidas por _Oracle_ y que se pueden usar en cualquier programa PL/SQL. Algunos ejemplos de excepciones predefinidas son: **NO_DATA_FOUND**, **TOO_MANY_ROWS**, **INVALID_NUMBER**, etc.
2. Excepciones definidas por el usuario: Son las excepciones que se crean en el propio programa PL/SQL para manejar situaciones específicas.

Para manejar excepciones en PL/SQL, se utiliza la estructura **TRY-CATCH**. El bloque **TRY** contiene el código que se ejecutará normalmente, y el bloque **CATCH** contiene el código que manejará las excepciones. El código en el bloque CATCH se ejecutará solo si ocurre una excepción en el bloque TRY.

A continuación se mostrará un ejemplo en el que se use el **TRY-CATCH**:

    DECLARE
        saldo NUMBER(10) := 1000;
        retiro NUMBER(10) := 2000;
    BEGIN
        IF retiro > saldo THEN
            RAISE_APPLICATION_ERROR(-20001, 'Fondos insuficientes');
        ELSE
            saldo := saldo - retiro;
            DBMS_OUTPUT.PUT_LINE('Retiro exitoso. Nuevo saldo: ' || saldo);
        END IF;
        EXCEPTION
        WHEN OTHERS THEN
            DBMS_OUTPUT.PUT_LINE('Error: ' || SQLCODE || ' - ' || SQLERRM);
    END;

En este código se realiza una verificación para asegurarse de que hay suficientes fondos para el retiro. Si no hay suficientes fondos, se lanza una excepción personalizada utilizando la función **RAISE_APPLICATION_ERROR**. Si la verificación es exitosa, se realiza el retiro y se muestra un mensaje de éxito.

_________________________________________________

6. ¿Qué son los cursores de SQL y cómo se declaran?  ilustre esto con un ejemplo.

## _6ta pregunta:_

Los cursores en SQL son objetos que permiten recorrer y manipular los resultados de una consulta en una fila por vez. Los cursores son útiles cuando se necesita procesar los resultados de una consulta de forma individual o cuando se necesita acceder a una fila específica de los resultados.

Para declarar un cursor en PL/SQL, se debe seguir los siguientes pasos:

1. Definir el cursor: se debe definir una consulta SQL que devuelva los datos que se desean procesar.

2. Declarar el cursor: se declara el cursor utilizando la sintaxis **CURSOR nombre_cursor IS consulta_sql;** , donde **nombre_cursor** es el nombre que se le dará al cursor y **consulta_sql** es la consulta SQL que se definió en el primer paso.

3. Abrir el cursor: se utiliza la sentencia **OPEN nombre_cursor;** para abrir el cursor y ejecutar la consulta SQL.

4. Recorrer el cursor: se utiliza un loop para recorrer los resultados del cursor fila por fila. Dentro del loop, se utilizan las sentencias **FETCH nombre_cursor INTO variable1, variable2, ...;** para obtener los valores de las columnas de la fila actual del cursor y asignarlos a variables.

5. Cerrar el cursor: se utiliza la sentencia **CLOSE nombre_cursor;** para cerrar el cursor y liberar los recursos utilizados.

A continuación se muestra un ejemplo de declaración y uso de un cursor en PL/SQL:


    DECLARE
        CURSOR c_empleados IS
            SELECT nombre, salario FROM empleados WHERE departamento = 'Ventas';
        v_nombre VARCHAR2(50);
        v_salario NUMBER(10,2);
        BEGIN
            OPEN c_empleados;
            LOOP
                FETCH c_empleados INTO v_nombre, v_salario;
                EXIT WHEN c_empleados%NOTFOUND;
                DBMS_OUTPUT.PUT_LINE('Nombre: ' || v_nombre || ', Salario: ' || v_salario);
            END LOOP;
        CLOSE c_empleados;
    END;


En este ejemplo, se define un cursor **c_empleados** que selecciona los nombres y salarios de los empleados del departamento de Ventas. Se utiliza un loop para recorrer los resultados del cursor y se muestra el nombre y salario de cada empleado utilizando la función **DBMS_OUTPUT.PUT_LINE**. Finalmente, se cierra el cursor.

_________________________________________________

7. ¿Qué son los triggers y para qué pueden ser utilizados?

## _7ma pregunta:_

En PL/SQL, los triggers son procedimientos almacenados que se ejecutan automáticamente en respuesta a ciertos eventos, como la inserción, actualización o eliminación de registros en una tabla. Un trigger se define para activarse antes o después del evento y puede contener código PL/SQL personalizado para manipular los datos o realizar otras acciones.

Los triggers pueden ser utilizados para una variedad de propósitos, incluyendo la validación de datos, la actualización automática de campos relacionados, la auditoría de cambios y la implementación de restricciones de seguridad. Algunos ejemplos de uso común de los triggers son:

- **Verificación de restricciones de integridad:** se pueden crear triggers para verificar que ciertas condiciones se cumplan antes de permitir una inserción, actualización o eliminación de registros en una tabla.
- **Actualización de campos relacionados:** si una tabla tiene campos relacionados con otra tabla, se pueden crear triggers para actualizar automáticamente esos campos cuando se realice una operación en la tabla principal.
- **Auditoría de cambios:** los triggers también se pueden utilizar para registrar los cambios realizados en una tabla para fines de auditoría. 
- **Restricciones de seguridad:** los triggers se pueden utilizar para implementar restricciones de seguridad adicionales en una base de datos.

Para crear un trigger en PL/SQL, se utiliza la siguiente sintaxis:

    CREATE [OR REPLACE] TRIGGER nombre_trigger
    {BEFORE | AFTER} {INSERT | UPDATE | DELETE}
    ON nombre_tabla
    [REFERENCING OLD AS old NEW AS new]
    [FOR EACH ROW]
    DECLARE
        -- Declaración de variables y constantes
    BEGIN
        -- Código PL/SQL
    EXCEPTION
        -- Manejo de excepciones
    END;

Por ejemplo, el siguiente trigger se activa antes de cada inserción en una tabla llamada **ventas** y verifica que el valor de la columna **precio** no sea negativo:

    CREATE OR REPLACE TRIGGER validar_precio
    BEFORE INSERT ON ventas
    FOR EACH ROW
    DECLARE
        precio_valido EXCEPTION;
    BEGIN
        IF :NEW.precio < 0 THEN
            RAISE precio_valido;
        END IF;
    EXCEPTION
        WHEN precio_valido THEN
            RAISE_APPLICATION_ERROR(-20001, 'El precio no puede ser negativo');
    END;

Este trigger define una excepción personalizada llamada **precio_valido** que se eleva si el valor de la columna **precio** es negativo. Luego, se utiliza un bloque **`BEGIN`...`END`** para escribir el código PL/SQL que verifica la condición y maneja la excepción si se produce. Si se eleva la excepción **precio_valido**, se utiliza la función **RAISE_APPLICATION_ERROR** para devolver un mensaje de error personalizado al usuario.

_________________________________________________

8. Usando ejemplos, explique las diferencias entre los triggers  BEFORE, AFTER, e  INSTEAD OF.

## _8va pregunta:_

En PL/SQL, los triggers son objetos que se utilizan para detectar y responder a eventos específicos que ocurren en una tabla o vista, como INSERT, UPDATE y DELETE. Los triggers pueden ser de tres tipos diferentes: BEFORE, AFTER e INSTEAD OF. A continuación, se explican las diferencias entre estos tres tipos de triggers mediante ejemplos.

1. **TRIGGER BEFORE:**

    Un trigger BEFORE se dispara antes de que ocurra una acción en una tabla o vista. El trigger puede ser utilizado para validar los datos que se están ingresando o para hacer cambios en los datos antes de que sean almacenados en la tabla. 


        CREATE OR REPLACE TRIGGER before_insert_productos
        BEFORE INSERT ON productos
        FOR EACH ROW
        DECLARE
            -- Declaración de variables
        BEGIN
            -- Validación de precio
            IF :NEW.precio <= 0 THEN
                RAISE_APPLICATION_ERROR(-20001, 'El precio debe ser mayor a cero.');
            END IF;
        END;
        /


2. **TRIGGER AFTER:**

    Un trigger AFTER se dispara después de que ocurre una acción en una tabla o vista. El trigger puede ser utilizado para realizar acciones adicionales después de que los datos han sido insertados, actualizados o eliminados de la tabla.

        CREATE OR REPLACE TRIGGER after_update_productos
        AFTER UPDATE ON productos
        FOR EACH ROW
        DECLARE
            -- Declaración de variables
        BEGIN
            -- Actualización de tabla de ventas
            UPDATE ventas
            SET cantidad = cantidad + :NEW.cantidad - :OLD.cantidad
            WHERE producto_id = :NEW.producto_id;
        END;
        /

3. **TRIGGER INSTEAD OF:**

    Un trigger INSTEAD OF se dispara en lugar de la operación INSERT, UPDATE o DELETE en una vista. El trigger puede ser utilizado para controlar cómo se manejan los datos en una vista que está basada en varias tablas. 

        CREATE OR REPLACE TRIGGER instead_of_update_pedidos_clientes
        INSTEAD OF UPDATE ON pedidos_clientes_v
        FOR EACH ROW
        DECLARE
            -- Declaración de variables
        BEGIN
            -- Actualización de tabla de clientes
            UPDATE clientes
            SET nombre = :NEW.nombre, direccion = :NEW.direccion
            WHERE cliente_id = :NEW.cliente_id;

            -- Actualización
        END;
        /