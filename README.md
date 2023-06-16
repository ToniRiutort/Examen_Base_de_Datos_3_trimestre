# Examen_Base_de_Datos_3_trimestre

## Enunciados y soluciones

1. Escribe una sentencia SQL que muestre el valor de todos los atributos de todos los registros de la tabla Customers.

SELECT * FROM customers;

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/abc667fd-8f2a-4ae9-93b7-de5b6b4730b0)

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/76e1ef16-9f8e-494a-853e-e5ed84810bfb)

2. Escribe una sentencia SQL que muestre el valor máximo de todos los atributos de todos los registros de la tabla Customers

Yo he puesto que la querry tendria que ser SELECT MAX(*) FROM customers; pero da error

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/7731dcce-627d-4dce-bc27-25a11a8bae87)

SELECT max(CustomerID),max(CustomerName),max(ContactName),max(Address),max(City),max(PostalCode),max(Country) FROM customers;

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/a55efa70-25b9-4ccf-94fe-ce7afb5d5b57)

3. Escribe una sentencia SQL que muestre solo los valores de los atributos CustomerName y City de todos los registros de la tabla Customers.

SELECT CustomerName,City FROM customers;

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/68668e0a-666a-4ecc-a294-f72e493a5504)

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/56695075-058c-4670-99fd-79ac25e15fb7)

4. Escribe una sentencia SQL para la tabla Customers que muestre todos los valores diferentes del atributo Country, sin mostrar duplicados.

SELECT DISTINCT Country FROM customers; Hay que usar el DISTINCT para que no duplique resultados. 

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/357b5214-ceb5-42c3-ab15-0d46c12f7e11)

5. Escribe una sentencia SQL que muestre los valores de todos los atributos de la tabla Customers, pero solo de los registros donde el atributo Country valga exactamente Mexico.

SELECT * FROM customers WHERE Country = "Mexico";

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/1edc813b-b3e3-46b7-8961-49976da0f8e9)

6. Escribe una sentencia SQL que puestre los valores de todos los atributos de la tabla Customers, pero solo de los registros donde el atributo Country valga Germany y simultáneamente el atributo City valga Berlin.

SELECT * FROM customers WHERE Country = "Germany" AND City = "Berlin";

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/e404e2f7-25df-4d78-9a1d-c5e5ad04b7f1)

7. Escribe una sentencia SQL que muestre el nombre de todos los productos (ProductName) y el nombre de la categoría (CategorieName) a la que pertenece cada uno de los productos. Las categorías se encuentran en la tabla Categories y los productos en la tabla Products.

SELECT products.ProductName,CategoryName FROM categories
INNER JOIN products ON categories.CategoryID= products.CategoryID;

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/f2770164-195c-402e-bdcb-afd6ce14a11e)

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/370a6fff-3aec-41a7-98f5-1feb2233e108)

8. Escribe una sentencia SQL que muestre el nombre de todos los productos (ProductName) y el nombre de las categorías (CategorieName) a las que pertenecen cada uno de los productos así como también el nombre del proveedir (Suppliers). Las categorías se encuentran a la tabla Categories, los productos a la tabla Products y los proveedores a la tabla Suppliers.

SELECT products.ProductName,CategoryName, suppliers.SupplierName FROM categories
INNER JOIN products ON categories.CategoryID= products.CategoryID
INNER JOIN suppliers ON products.SupplierID = suppliers.SupplierID;

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/f8f9abbc-d9fd-4e98-82d8-ec7ea7c17053)

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/9aa38238-0778-4786-a84f-6900774b1211)

9. Escribe una sentencia SQL que cuente el número de productos (Products) por categorías (Categories). Se tienen que mostrar dos columnas, CategorieName y el contador. Solo tienen que aparecer las categorías con productos. Las categorías se encuentran a la tabla Categories y los productos a la tabla Products.

SELECT CategoryName, COUNT(products.ProductID) FROM categories
RIGHT JOIN products ON categories.CategoryID= products.CategoryID
GROUP BY categories.CategoryID;

Utilizo el right join para que no tenga en cuenta lo vacios de categories.

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/c1386440-7cef-45fe-85ad-16813fba4fcb)

10. Escribe una sentencia SQL que cuente el número de productos (Products) por categorías (Categories). Solamente nos interesa contar el producto que empieza por P. Tienen que aparecer las categorías que no tienen productos. Las categorías se encuentran a la tabla Categories, los productos a la tabla Products.

SELECT CategoryName, COUNT(products.ProductID) FROM categories
LEFT JOIN products ON categories.CategoryID= products.CategoryID
WHERE ProductName LIKE 'P%'
GROUP BY categories.CategoryID;

Utilizo el left join para que si tenga en cuenta lo vacios de categories.

![image](https://github.com/ToniRiutort/Examen_Base_de_Datos_3_trimestre/assets/104781981/64a32cd1-3733-411d-84c1-bf2e1118b32d)
