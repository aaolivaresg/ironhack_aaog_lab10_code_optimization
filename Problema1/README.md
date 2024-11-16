
## 1. Codigo javaScript 

### Código Original:
```javascript
// Inefficient loop handling and excessive DOM manipulation
function updateList(items) {
  let list = document.getElementById("itemList");
  list.innerHTML = ""; // Limpia la lista antes de actualizar
  for (let i = 0; i < items.length; i++) {
    let listItem = document.createElement("li");
    listItem.innerHTML = items[i];
    list.appendChild(listItem);
  }
}
```
---

### Problema Identificado:
* Manipulación innecesaria del DOM (document) dentro del bucle.

---

### Optimización:

```javascript
function updateList(items) {
let list = document.getElementById("itemList");
list.innerHTML = ""; // Limpia la lista antes de actualizar

// Crear un fragmento de documento para reducir manipulaciones del DOM
let fragment = document.createDocumentFragment();
items.forEach(item => {
let listItem = document.createElement("li");
listItem.innerHTML = item;
fragment.appendChild(listItem);
});
list.appendChild(fragment); // Realizar un solo re-renderizado
}
```

###  Cambios Realizados:

* En javascript se puede usar el objeto DocumentFragment quitar manipulaciones del DOM hasta que el bucle haya terminado.
* Se utiliza forEach, lo cual hace el código más legible y mantiene la misma lógica.

### Beneficio:

* Reducción significativa del costo computacional al minimizar los accesos directos al DOM.
* Mejora la escalabilidad para listas más grandes.
