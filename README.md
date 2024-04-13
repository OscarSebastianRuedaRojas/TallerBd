# Consultas sobre una tabla

1. #### Lista el nombre de todos los productos que hay en la tabla producto:

```sql
SELECT nombre
	FROM public.producto;
```

![image-20240412062213123](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412062213123.png)

2. #### Lista los nombres y los precios de todos los productos de la tabla producto:

```sql
SELECT nombre, precio
	FROM public.producto;
```

![image-20240412062424247](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412062424247.png)

3. #### Lista todas las columnas de la tabla producto.

```sql
SELECT codigo ,nombre, precio, codigo_fabricante
	FROM public.producto;
```

![image-20240412062636196](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412062636196.png)

4. #### Lista el nombre de los productos, el precio en euros y el precio en dólares

  #### estadounidenses (USD).

```sql
SELECT nombre, precio as USD, ROUND(CAST(precio AS numeric) * 1.16, 2) as EUR
	FROM public.producto;
```

![image-20240412063652576](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412063652576.png)

5. #### Lista el nombre de los productos, el precio en euros y el precio en dólares estadounidenses (USD). Utiliza los siguientes alias para las columnas: nombre de producto, euros, dólares:

  ```sql
  SELECT nombre as nombre_de_producto, precio as Dolares, TRUNC(CAST(precio AS numeric) * 1.16, 2) as Euros
  	FROM public.producto;
  ```

  

![image-20240412063940015](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412063940015.png)

6. #### Lista los nombres y los precios de todos los productos de la tabla producto, convirtiendo los nombres a mayúscula.

   ```sql
   SELECT UPPER(nombre) as nombre_de_producto, precio 
   	FROM public.producto;
   ```

   

![image-20240412064345204](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412064345204.png)

7. #### Lista los nombres y los precios de todos los productos de la tabla producto, convirtiendo los nombres a minúscula.

```sql
SELECT LOWER(nombre) as nombre_de_producto, precio 
	FROM public.producto;
```



![image-20240412064524490](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412064524490.png)

8. #### Lista el nombre de todos los fabricantes en una columna, y en otra columna obtenga en mayúsculas los dos primeros caracteres del nombre del
fabricante.

```sql
SELECT nombre, LEFT(UPPER(nombre), 2) as iniciales
	FROM public.fabricante;
```

![image-20240412065058219](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412065058219.png)

9. #### Lista los nombres y los precios de todos los productos de la tabla producto, redondeando el valor del precio.

```sql
SELECT nombre , ROUND(CAST(precio as numeric), 0) 
	FROM public.producto;
```

![image-20240412065457678](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412065457678.png)

10. #### Lista los nombres y los precios de todos los productos de la tabla producto, truncando el valor del precio para mostrarlo sin ninguna cifra decimal.

```sql
SELECT nombre , TRUNC(precio) 
	FROM public.producto;
```

![image-20240412065707140](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412065707140.png)

11. #### Lista el identificador de los fabricantes que tienen productos en la tabla producto.

```sql
SELECT nombre, codigo_fabricante
	FROM public.producto;
```

![image-20240412065936800](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412065936800.png)

12. #### Lista el identificador de los fabricantes que tienen productos en la tabla producto, eliminando los identificadores que aparecen repetidos.

```sql
SELECT DISTINCT codigo_fabricante 
	FROM public.producto;
```

![image-20240412070210055](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412070210055.png)

13. #### Lista los nombres de los fabricantes ordenados de forma ascendente.

```sql
SELECT nombre
	FROM public.fabricante
	ORDER BY nombre ASC
```

![image-20240412070520562](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412070520562.png)

14. #### Lista los nombres de los fabricantes ordenados de forma descendente.

```sql
SELECT nombre
	FROM public.fabricante
	ORDER BY nombre DESC
```

![image-20240412070628347](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412070628347.png)

15. #### Lista los nombres de los productos ordenados en primer lugar por el nombre de forma ascendente y en segundo lugar por el precio de forma
descendente.

```sql
SELECT nombre, precio
	FROM public.producto
ORDER BY nombre ASC, precio DESC;
```

![image-20240412072210492](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412072210492.png)

16. #### Devuelve una lista con las 5 primeras filas de la tabla fabricante.

```sql
SELECT nombre
	FROM public.fabricante
LIMIT 5;
```

![image-20240412082125627](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412082125627.png)

17. #### Devuelve una lista con 2 filas a partir de la cuarta fila de la tabla fabricante. La cuarta fila también se debe incluir en la respuesta.

```sql
SELECT nombre
	FROM public.fabricante
OFFSET 3
LIMIT 4;
```

![image-20240412072813755](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412072813755.png)

18. #### Lista el nombre y el precio del producto más barato. (Utilice solamente las cláusulas ORDER BY y LIMIT)

```sql
SELECT nombre, precio
	FROM public.producto
ORDER BY precio ASC
LIMIT 1;
```

![image-20240412073006582](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412073006582.png)

19. #### Lista el nombre y el precio del producto más caro. (Utilice solamente las cláusulas ORDER BY y LIMIT)

    ```sql
    SELECT nombre, precio
    	FROM public.producto
    ORDER BY precio DESC
    LIMIT 1;
    ```

    

![image-20240412075046794](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412075046794.png)

20. #### Lista el nombre de todos los productos del fabricante cuyo identificador de fabricante es igual a 2.

    ```sql
    SELECT nombre, precio, codigo
     from producto
     where codigo_fabricante = 2
    ```

    ![image-20240412075617218](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412075617218.png)

21. #### Lista el nombre de los productos que tienen un precio menor o igual a 120€.

    ```sql
    SELECT nombre
    	from public.producto
    	where precio<=120
    ```

    ![image-20240412080003547](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412080003547.png)

22. #### Lista el nombre de los productos que tienen un precio mayor o igual a 400€.

```sql
SELECT nombre
	from public.producto
	where precio>=400
```

![image-20240412080118272](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412080118272.png)

23. #### Lista el nombre de los productos que no tienen un precio mayor o igual a 400€.

```sql
SELECT nombre
	from public.producto
	where precio <400
```

![image-20240412080928736](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412080928736.png)

24. #### Lista todos los productos que tengan un precio entre 80€ y 300€. Sin utilizar el operador BETWEEN.

```sql
SELECT nombre, precio
	from public.producto
	where precio > 80 AND precio < 300
```

![image-20240412081247720](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412081247720.png)

25. #### Lista todos los productos que tengan un precio entre 60€ y 200€. Utilizando el operador BETWEEN.

```sql
SELECT nombre, precio
	from public.producto
	where precio between 60 and 200
```

![image-20240412081409351](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412081409351.png)

26. #### Lista todos los productos que tengan un precio mayor que 200€ y que el identificador de fabricante sea igual a 6.

```sql
SELECT nombre, precio, codigo_fabricante
	FROM producto
	where precio > 200 and codigo_fabricante = 6
```

![image-20240412082044804](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412082044804.png)

27. #### Lista todos los productos donde el identificador de fabricante sea 1, 3 o 5. Sin utilizar el operador IN.

```sql
SELECT nombre
FROM public.producto
WHERE codigo_fabricante = 1 OR codigo_fabricante = 3 OR codigo_fabricante = 5;
```

![image-20240412082449791](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412082449791.png)

28. #### Lista todos los productos donde el identificador de fabricante sea 1, 3 o 5. Utilizando el operador IN.

```sql
SELECT nombre
FROM public.producto
WHERE codigo_fabricante in ( 1, 3, 5);
```

![image-20240412083802299](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412083802299.png)

29. #### Lista el nombre y el precio de los productos en céntimos (Habrá que multiplicar por 100 el valor del precio). Cree un alias para la columna que
contiene el precio que se llame céntimos.

```sql
SELECT nombre, precio, precio*100 as centimos
FROM public.producto
```

![image-20240412084106776](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412084106776.png)

30. #### Lista los nombres de los fabricantes cuyo nombre empiece por la letra S.

```sql
SELECT nombre, LEFT(nombre, 1) as inicial
FROM public.fabricante
WHERE LEFT(nombre, 1) = 'S';
```

![image-20240412084438573](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412084438573.png)

31. #### Lista los nombres de los fabricantes cuyo nombre termine por la vocal e.

```sql
SELECT nombre, RIGHT(nombre, 1) as inicial
FROM public.fabricante
WHERE RIGHT(nombre, 1) = 'e';
```

![image-20240412084617866](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412084617866.png)

32. #### Lista los nombres de los fabricantes cuyo nombre contenga el carácter w.

```sql
SELECT nombre
FROM public.fabricante
WHERE nombre LIKE '%w%';
```

![image-20240412084950744](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412084950744.png)

33. #### Lista los nombres de los fabricantes cuyo nombre sea de 4 caracteres.

```sql
SELECT nombre
FROM public.fabricante
WHERE LENGTH(nombre) = 4;

```

![image-20240412085135253](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412085135253.png)

34. #### Devuelve una lista con el nombre de todos los productos que contienen la cadena Portátil en el nombre.

```sql
SELECT nombre
FROM public.producto
WHERE nombre LIKE '%Portatil%';
```

![image-20240412085259627](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412085259627.png)

35. #### Devuelve una lista con el nombre de todos los productos que contienen la cadena Monitor en el nombre y tienen un precio inferior a 215 €.

```sql
SELECT nombre
FROM public.producto
WHERE nombre LIKE '%Monitor%' AND precio<215;
```

![image-20240412085555761](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412085555761.png)

36. #### Lista el nombre y el precio de todos los productos que tengan un precio mayor o igual a 180€. Ordene el resultado en primer lugar por el precio (en orden descendente) y en segundo lugar por el nombre (en orden
ascendente).

```sql
SELECT precio, nombre
FROM public.producto
WHERE precio>=180
ORDER BY precio DESC, nombre ASC
;
```

![image-20240412085850083](C:\Users\senit\AppData\Roaming\Typora\typora-user-images\image-20240412085850083.png)