# 1.1 Protocolo del Cliente
## La clase Cliente tiene el siguiente protocolo ¿Como puede mejorarlo?
```java
        //Retorna el límite de crédito del cliente
        public double lmtCrdt() {...

        //Retorna el monto facturado al cliente desde la fecha f1 a la fecha f2
        protected double mtFcE(LocalDate f1, LocalDate f2) {...
 
        //Retorna el monto cobrado al cliente desde la fecha f1 a la fecha f2
        private double mtCbE(LocalDate f1, LocalDate f2) {...
```
## Resolucion usando refacoring 
+ La firma de los metodos ```lmtCrdt(), mtFcE() y mtCbE()``` no describe la fucionalidad de los mismos, los metodos deben tener un nombre descriptivo de su funcionalidad.
    ``` java
        //Retorna el límite de crédito del cliente
        public double limiteDeCredito(){...}
        //Retorna el monto facturado al cliente desde la fecha f1 a la fecha f2
        protected double montoFacturadoEntre(LocalDate fechaDesde, LocalDate fechaHasta){...}
        //Retorna el monto cobrado al cliente desde la fecha f1 a la fecha f2
        private double montoACobrarEntre(LocalDate fechaDesde, LocalDate fechaHasta){...}
    ```
## 1.2 Participacion en proyectos   
Revisar el siguiente diseño inicial (figura 1), se decidio realizar un cambio para evitar lo que se consideraba un mal olor El diseño modificado se muestra en l figura 2. Indique que tipo de cambio se realizo y si lo considera apropiado. Justifique su respuesta.
![alt text](participacioEnProyectos.png)
### Diseño inicial - Comentarios
 * La clase `Proyecto` solo actua como una clase de datos
 * El atributo `id` de `Persona` esta declarado como publico lo que anula la encapsulacion de la clase.
 * El metodo `participaEnProyecto(p:Proyecto):boolean`:
    * No de beria ser un metodo de la clase `Persona` lo que resulta en un **Feature envi** 
    * La variable `p:Proyecto` es poco descriptiva
### Diseño revisado - Comentarios
* Hora el metodo `participa(p:Persona):boolean` se queda declarado en la clase `Proyecto` solucionando la mala delegacion y **Feature envi** 
* Aun quedan malos olores en la nueva implementacion: 
    * La variable `id` en la clase `Persona`permanece publica violando el encapsulamiento

## 1.3 Calculos 
Analice el codigo que se muestra a continuacion. Indique que *code smells* encuentra y como pueden corregirse.
``` java
    public void imprimirValores() {
        int totalEdades = 0;
        double promedioEdades = 0;
        double totalSalarios = 0;
        
        for (Empleado empleado : personal) {
            totalEdades = totalEdades + empleado.getEdad();
            totalSalarios = totalSalarios + empleado.getSalario();
        }
        promedioEdades = totalEdades / personal.size();
        String message = String.format("El promedio de las edades es %s y el total de
        salarios es %s", promedioEdades, totalSalarios);
        System.out.println(message);
    }
```
### Resolucion usando refactoring
+ *Code Smells* encontrados:
    + EL metodo `imprimirValores()` realiza dos tareas distintas, aunque se cumple con la descripcion y objetivo de la firma del metodo no es extensible ya que si se quisiera solo imprimir el promedio de salario o solo el promedio de edades esto no seria lo correcto
    + Ademas la variable personal no se encuentra en el metodo.
+ Sugerencias de correcciones:
    + Separar los metodos con una tarea en especifico
    + Renombrar el metodo con una descripcion clara 
        Ejemplo: `imprimirPromedioDeEdad()` y `imprimirSalarioPromedio()`