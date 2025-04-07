# 1.1 Protocolo del Cliente
## La clase Cliente tiene el siguiente protocolo ¿Como puede mejorarlo?´´´ java

    ``` java
                /** 
        * Retorna el límite de crédito del cliente
        */
        public double lmtCrdt() {...

        /** 
        * Retorna el monto facturado al cliente desde la fecha f1 a la fecha f2
        */
        protected double mtFcE(LocalDate f1, LocalDate f2) {...

        /** 
        * Retorna el monto cobrado al cliente desde la fecha f1 a la fecha f2
        */
        private double mtCbE(LocalDate f1, LocalDate f2) {...
    ```
## Resolucion usando refacoring 
+ La firma de los metodos ``` java lmtCrdt(), mtFcE() y mtCbE()``` no describe la fucionalidad de los mismos, los metodos deben tener un nombre descriptivo de su funcionalidad.
    ``` java
        //Retorna el límite de crédito del cliente
        public double limiteDeCredito(){...}
        //Retorna el monto facturado al cliente desde la fecha f1 a la fecha f2
        protected double montoFacturadoEntre(LocalDate fechaDesde, LocalDate fechaHasta){...}
        //Retorna el monto cobrado al cliente desde la fecha f1 a la fecha f2
        private double montoACobrarEntre(LocalDate fechaDesde, LocalDate fechaHasta){...}
    ```

