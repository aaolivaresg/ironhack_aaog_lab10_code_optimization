# 3. Código en C#

``` csharp
// Unnecessary computations in data processing
public List<int> ProcessData(List<int> data) {
List<int> result = new List<int>();
foreach (var d in data) {
if (d % 2 == 0) {
result.Add(d * 2);
} else {
result.Add(d * 3);
}
}
return result;
}
```
---
### Problema Identificado:

El procesamiento es secuencial, lo que puede ser ineficiente para grandes volúmenes de datos.
No aprovecha capacidades de paralelismo o pipelines para optimizar las operaciones.

---
### Optimización:

``` csharp
using System.Linq;

public List<int> ProcessData(List<int> data) {
return data.AsParallel()
.Select(d => d % 2 == 0 ? d * 2 : d * 3)
.ToList();
}
```
---
### Cambios Realizados:

* Uso de AsParallel para procesar los datos en paralelo.
---

### Beneficio:

* Mejora el rendimiento en conjuntos de datos grandes al distribuir el trabajo entre varios hilos.
* Código más legible y mantenible.
