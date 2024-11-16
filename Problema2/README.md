# 2. Código Java

```java
// Redundant database queries
public class ProductLoader {
public List<Product> loadProducts() {
List<Product> products = new ArrayList<>();
for (int id = 1; id <= 100; id++) {
products.add(database.getProductById(id));
}
return products;
}
}
``` 

---
### Problema Identificado:

* ealiza 100 consultas separadas a la base de datos, lo cual genera un alto costo en tiempo y recursos.

---
### Optimización:

```java
public class ProductLoader {
public List<Product> loadProducts() {
// Realizar una única consulta para obtener los 100 productos
return database.getProductsInRange(1, 100);
}
}

public List<Product> getProductsInRange(int startId, int endId) {
   
    // regresamos la información de un query así: "SELECT id, name, price FROM products WHERE id BETWEEN ? AND ?";
}
```
---

### Cambios Realizados:

* En lugar de iterar y realizar una consulta por producto, se utiliza una única consulta para recuperar todos los productos dentro del rango especificado.
* Delegar la lógica de optimización a la base de datos mediante un método como getProductsInRange.
---
### Beneficio:

* Reduce el número de llamadas a la base de datos de 100 a 1, disminuyendo la latencia y la carga del servidor.
* Aumenta  el rendimiento al procesar datos en bloque.
