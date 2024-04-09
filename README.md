# SQL-Python

#Base de datos Northwind

Esta es una versión de la base de datos de ejemplo Northwind de Microsoft Access 2000, rediseñada para SQLite3.

La base de datos de ejemplo Northwind se proporcionó con Microsoft Access como un esquema de tutorial para administrar clientes, pedidos, inventario, compras, proveedores, envíos y empleados de pequeñas empresas. Northwind es un excelente esquema de tutorial para un ERP de pequeña empresa, con clientes, pedidos, inventario, compras, proveedores, envíos, empleados y contabilidad de entrada única.

#Consultas 

Como primer consulta obtendremos los 10 productos más rentables de acuerdo a su ganancia total.
'''
    SELECT ProductName, SUM(Price * Quantity) as Revenue
    FROM OrderDetails od
    JOIN Products p ON p.ProductID = od.ProductID
    GROUP BY od.ProductID
    ORDER BY Revenue DESC
    LIMIT 10
'''

imagen

Podemos observar que el producto que genera más ganancia es Côte de Blaye por mucho.

Ahora obtengamos los empleados más efectivos de la base de datos, mediante la siguiente consulta.

'''
    SELECT FirstName || " " || LastName as Employee, COUNT(*) as Total
    FROM Orders o
    JOIN Employees e ON e.EmployeeID = o.EmployeeID
    GROUP BY o.EmployeeID
    ORDER BY Total DESC
    LIMIT 10
'''

imagen

Ya que podemos ver cuáles son los más efectivos, como Maragaret Peacock, también nos interesa saber cuáles son los menos efectivos ya que estos empleados necesitan que se les preste más atención para decisiones futuras. La consulta que nos permite hacer esto es la siquiente.

'''
    SELECT FirstName || " " || LastName as Employee, COUNT(*) as Total
    FROM Orders o
    JOIN Employees e ON e.EmployeeID = o.EmployeeID
    GROUP BY o.EmployeeID
    ORDER BY Total ASC
    LIMIT 3
'''

imagen

Así vemos que el empleado menos efectivo es Anne Dodsworth con 6 ventas.
