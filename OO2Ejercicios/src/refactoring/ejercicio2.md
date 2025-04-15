# Ejercicio 2
Para cada una de las siguientes situaciones, realice en forma iterativa los siguientes pasos:
1. Indique mal olor
2. Indique el refactoring que lo corrige
3. Aplique el refactoring, mostrando el resultado final(codigo y/o diseño segun corresponda).
> [!WARNING]
> Si vuelve a encontrar un mal olor vuelva al paso 1.
## 2.1 Empleados 
``` java
    public Class EmpleadoTemporario{
        public String nombre;
        public String apellido;
        public double sueldoBasico = 0 ;
        public double horasTrabajadas = 0;
        public int cantidadHijos = 0;
        //...
        public double sueldo(){
            return this.sueldoBasico
                + (this.horasTrabajadas * 500)
                + (this.cantidadHijos * 1000)
                - (this.sueldoBasico * 0.13);
        }
    }
    public Class EmpleadoPlanta{
        public String nombre;
        public String apellido;
        public double sueldoBasico = 0 ;
        public int cantidadHijos = 0; 
        //...
        public double sueldo(){
            return this.sueldoBasico
                + (this.cantidadHijos * 2000)
                - (this.sueldoBasico * 0.13);
        }
    }
    public Class EmpleadoPasante{
        public String nombre;
        public String apellido;
        public double sueldoBasico = 0 ; 
        //...
        public double sueldo(){
            return this.sueldoBasico - (this.sueldoBasico * 0.13);
        }
    }
```
### Resoluciones 
+  Code Smells encontrados
    + Codigo y variables duplicadas
        El metodo `sueldo()` y las variables de instancia `nombre`,`apellido` y `sueldoBasico` se encuentran repetidos en todas las clases por lo que se recomienda hace un **Extract Class** de forma que todas las similitudes queden en una solo clase y ahora estas clases pasaran a ser subclases de la nueva **Superclase**, ademas aplicamos el refactoring **Pull up Method y Pull Field**
    + violacion de encapsulacion
        Las variables de instancias pasadas a la SuperClase deben ser midificadas como privadas para que no se viole la encapsulacion, almodificarlas a estado `private` las subclases no podran acceder a ella por lo cual se las debe modificar a `protected`, esto se logra aplicando el refactoring **Encapsulate field**
