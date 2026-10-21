
# UNIDAD - 1 
## Clases genericas 
---
> Permiten que un tipo de datos sea un parametro en las definiciones de una clase ,interfaz o metodo 
>Estas clases son parte de lo que Java denomina programacion generica , que fue introducida en java 5 par para mejorar la seguridad de tipo y reducir el casting(cambiar un tipo de dato a otro) que es propenso a errores .
>COMO CASTERAR DIFERENTES TIPOS DE DATOS en java(investigar) :
```java
double n = 0,1;
int num = (int) 0,1;
```
## Ejemplo materia anterior 
```java 
String a = new String("Hola");
String b = new String("Hola");
String c = a;
System.out.printl(a==b);//FALSE
System.out.printl(a==c);//TRUE

a="HOLA MUNDO";
System.out.printl(c);
```
>String son inmutables = no se pueden modificar
>porque se dan esos errores de 0,1 + 0.2 me da 0.30000004 y asi 
## Clase Generica en  java 
```java
public class Box<T>{
    private T t ;

    public void set(T t){
        this.t = t;
    }

    public T get(){
        return t ;
    }
}
```
---
### Clase dos Progra 
## Tipos de datos 
---

>La programacion tradicional nos obliga a duplicar codigo para diferentes tiposd e datos 
>Se repite la logica 
>Aumenta el manteniiento 
>Escala mal con mas tipos
---
### tipos de datos
---

>Primitivos : Tipos basicos de datos que almacenan valores simples -- int , double,boolean
>Objetos : Instancias de clases que contienen datos y comportamiento -- String, Scanner, Arraylist
>Genericos : tipos parametrizados para mayor flexibilidad y seguridad -- <T>,<E>,<K,V>(Usado en mapas )

---
### Dato Generico
---

>Es un mecanismo que permite definir clases o metodos con un tipo parametrizado
>El termino generico significa tipos parametrizados usados para flexibilizar el codigo.
>Seguridad De Tipos -> Type Safety en tiempo de compilacion (es pasar de codigo a una clase que la pueda compilar  investigar mas )
>Reutilizaciòn - > Misma logica para multiples tipos de datos
>Evita Casting -> Elimina conversiones ineccesarias
>Independencia -> Codigo desacoplado del tipo de dato especifico 
##Ejemplo
```java
public class App {
    public static void main(String[] args)  {
        ArrayList lista = neew ArrayList<>();
        lista.add("Hola");
        lista.add("Mundo");
        lista.add(1);

        String dato1= (String)Lista.get(0);
        Object dato2 = lista.get(1);
        String dato3 = (String) lista.get(2);//Me da error no me permite castear 

        System.out.println(dato1);
        System.out.println(dato2);
        System.out.println(dato3);
    }
}
```
```java
// Este es el correcto la manera de hacerlo 
public class App {
    public static void main(String[] args)  {
        ArrayList<String> lista = neew ArrayList<>();
        lista.add("Hola");
        lista.add("Mundo");
        String dato1 = lista.get(0);
        String dato2 = lista.get(1);

        System.out.println(dato1);
        System.out.println(dato2);
    
    }
}
```

---
## Clase Generica
---
>Es necesario identificar el tipo Generico 
>Usa La notacion diamond "<>" que asi denomina java , infiero el tipo  a partir de la variable 
>class nombre-clase<lista-parametros-tipo>{....}
```java
class ArrayList<T>{
    //T es el pàrametro
    private T element;
}
``` 
>depende de los argumentos q yo de para definir el nombre de la clase si solo es de tipo T no varia ya sea entero o demas pero si es de tipo E  hay que definirlo arriba <T> -> <T,E>

---
### Reglas
---
>Prohibido -> Los tipos primitivos puros no son admitidos como argumentos de tipo 

```java
Caja<int>
Caja<Double>
```
---
## Metodos Genericos 
---
>Diseñados para trabajar con cualquier tipo de datos mediantw el uso de "type parameters", definidos en el momento de invocacion
```java 
public <T> calcular(T dato){  
}
```
---
### Tercer clase de Progra 
---
## METODO GENERICO 
---

>Declara sus propios parametros de tipo para relacionar lso datos que recibe y los devuelve 
>La declaracion aparece antes del tipo de retorno
>Si tengo atributos genericos la clase es generica pero tambien puede haber en una clase normal unos metodos genericos 
>El metodo puede pertenecer a una clase gnerica o a una clase que no lo sea.


```java
static<R> R identidad(R valor){
    return valor;
}
```
> <R> declara el parametro  R antes del nombre indica retorno 
>Declaracion previa;El parametro <T> debe declararse obligatoriamente antes del tipo de retorno
>Alcance aislado;El parametro T existe unica y exclusivamente dentro de la clase y se puede llamar afuer

---
## Cotas de tipado
---

>Limita los tipos admisibles y garantiza el acceso a operaciones especificas.

---
## Transformaciones mediante Fuction
---
>Fuction<A,B> e suna innterfaz de java que representa una operacion recibe un valor A y produce un resultado B.
>Su metodo principal es B apply(A valor)

```java
Fuction<String, Integer> longitud = texto -> texto.length();//En texto se gurada lo que llega  y la funcion flecha longitud es de tipo Fuction 
Integer cantidad = longitud.apply("Java");

```


```java
Fuction<String, Integer> longitud = t -> t.length();
int res = longitud .apply("Hola Mundo");

// es lo mismo que el siguiente metodo

public static   Integer applyFuction(String texto){
    return texto.lenght();
} 
int res2 = applyFunction("Hola Mundo");


// es lo mismo 

Function<String, Integer> longitud = t ->{
    int r = t.length();
    return r;
}
int res3= longitud.apply("Hola Mundo");
``` 

el `apply` es solo de la `fuction    `
"Q es record " investigar -> omitir setter y getters 

---
## Comparable: El orden naturald de lso objetos
---
Comparable<T> es una interfaz que permite definir como se ordenan los objetos de una clase.
Se implementa mediante compareTo(), que compara el objeto actual con otro 

Tabla 
dato | resultado 
Menor que 0 -> Va antes
Igual a 0 -> Empatan segun el criterio
Mayor que 0 -> Va despues 

La clase define el criterio de una cola vez; los algoritmos pueden utilizarlo para ordenar o encontrar al mayor elemento 

```java
public record Sensor(String id , String ubicacion) implements Conparable<Sensor>{
    @Override
    public int compareTo(Sensor otro){
        return id.compareTo(otro.id);
        //int r = id.compareTo(otro.id);
        //if(r!= 0){return r;}
        //return ubicacion.length().compareTo(otro.ubicacion.lenght());
        
    }
}
```

Ejemplo:
```java
Sensor sensor1 = new Sensor("S01", "Laboratorio");
Sensor sensor2 = new Sensor("S02", "Biblioteca");

if(sensor1.compareTo(sensor2) < 0 ){
    System.out.println("S01 va antes que S02");
}
```
---
## Boxing y Umboxing
---
Una clase envolvente que permite presentar ese valor mediante un objeto.Esta distincion importa porque los argumetosde de los genericos debe ser el tipo de referencia :
Una coleccion de enteros se declara `List<Integer>`, no -> `List<int>`

| Primitivo (`int`, `double`) | Envolvente (`Integer`, `Double`) |
|---|---|
| Valores directos  | Objetos de Heap |
| No permite `null` | Permite `null` |

Autoboxin, es la conversion automatica entre un primitivo y su 

Los envolventes son inmutables ;una operacion que cambia una variable integer no modifica el objeto anterior 
Ejemplo: 

```java
Integer c = new Integer(12); // pa no hacer esto

Integer cantidad = 12; //Autoboxing
int recuperada = cantidad;  // Unboxing

Integer explicita = Integer.valueOf(12);// otra manera de escribir 
int primitivo = explicita.intValue();
```
>Integer.valueOf(5).equals(Long.valueOf(5)) es false 
*equals* tambien exige compatibilidad de tipo.Si uno de los operandos de == es primitivo , puede  producirse unboxing con otro, con el riesgo de nulos mencionado 
El *parsing* interpreta una representacion textual .Integer.parseInt("12") devuelve int primitivo y puede lanzar NumberFormatException; no es boxing.
Integer.valueOf("12") interpreta texto y devuelve Object Integer.
valueOf -> Sirve para pasar de String a Integer
*Boxing* convertir un valor primitivo en su clase envoltorio , no interpretar texto
// foto del bryan 
````java
Codigo avac 
```
## For each
For each de indices para enfocarse en extraer una copia de la reo for recorre arreglos y objetos que implementan iterable  omitiendo la gestion manual ferencia de cada elemento.

```java
Integer[]  datos ={10, 20}
for(Integer valor : datos ){
    System.out.println(valor);
}
```

## Varargs (investigar mas )
*Varargs* permite recibir cero o mas argumentos mediante un parametro declarado con ... Dentor del metodo se trata como un arreglo.Debe existir como maximo un parametro varargs y ocpuar la ultima posicion
```java
static int contar(String... nombres){
    return nombres.length;
}
//contar()  --> devuelve 0
//contar("Ana", "Luis");  --> devuelve 2  
```

En java , el metodo main es el punto de entrada de una aplicacion.
En main (String[] args), representa lso argumentos de la linea de comandos; la sintaxis habitual del main ya recibe un arreglo.
```java
public class App {
    public static void main(String[] args) throws Exception {
        System.out.println("Hola mundo");
    }
}

```
El parámetro String[] args es un arreglo de cadenas que recibe
los argumentos enviados desde la terminal cuando
ejecutamos el programa.

````
# java Main Pablo 25 Cuenca
Java recibe tres argumentos:
0 | "Pablo" | args[0]
1 | "25"   | args[1]
2 | "Cuenca"  |  args[2]

Las dos declaracioens son validas 


```java
public static void main(String[] args)
public static void main(String... args)
```

En ambos casos , los argumentos llegan como un arreglo de cadenas.

###    Patrones de Diseño
>Son soluciones generales ,reutilizables y probadas para resolver problemas recurrentes en el diseño de sistemas orientados a objetos
> No son fragmentos de codiogo que se copian directamente , sino modelos de solucion que pueden adapatarse a diferentes contextos

mAPERde transformacion  --> Q es 
>Tipos
creacionales -> Controlan como se crean los objetos  --- Singleton,Factory Method Builder
estructurales -> Organizan las relaciones entre clases y objetos --- Adapter, Decarator , Facade
Comportamiento -> Como interactuan lso objetos y distribuyen responsabilidades --- Observer,Strategy,C

Ssitema de monitoreo de sensores
Factory Method: crear diferentes tipos de sensores sin depender de sus clases concretas
Observer: notifica automaticamente cuando cambia la lectura
Strategy: cambiar el algoritmo utilizado para procesar lecturas

Los patrones de dieño buscan mejorar la reutilizacion,mantenibilidad , flexibilidad y extensibilidad de software , reduciendo el acoplamiento entre componentes.
Un patron de diseño no es un algoritmo es una tecnica, se describe como organizar clases,objetos y responsabilidades para resolver un problema de diseño 

>Creacionsles 
Evitan que los clientes repitan logicas de construccion complejas que necesitan variar .No ocultan su uso de la palabra `new` , sino que encapsulan el proceso de instanciaciòn

## Patrones de Diseño: Creacionales

| Patrón | Intención Principal | Enfoque de Variación | Ejemplo de Uso |
|---|---|---|---|
| **Factory Method** | Una subclase decide qué producto concreto construir. | Operación de creación redefinible. | Exportador que elige formato (TXT, HTML). |
| **Abstract Factory** | Construir familias de productos relacionados. | Compatibilidad entre múltiples objetos. | Temas visuales (botón y menú oscuros). |
| **Builder** | Separar la construcción por etapas del uso del objeto. | Configuraciones complejas o validaciones. | Armado progresivo de un informe. |
| **Prototype** | Crear objetos clonando una instancia preconfigurada. | Evitar reconstruir desde cero. | Plantillas de documentos editables. |
| **Singleton** | Única instancia con punto de acceso global. | Centralizar un servicio o recurso. | Objeto de configuración inmutable. |


### 
>Factory Method
Una interfaz para crear objetos en una superclase, mientars permite a las subclases alterar el tipo de objetos que se crearan.
Subclase decida que producto va a construir mientras que la clase creadora conserva un procedimiento comun 
Metodo de creacion devuelve una abstraccion; cada sobreescritura suministra un prodcuto concreto 
### Problema
Un proceso recibe lineas de un identificador , valor y unidad.Un proovedor separa los campos con punto y como; otro usa tabulaciones .En ambos casos se deben omitir lineas vacias, interprestar datos, validar lecturas y señalar en que linea aparecio un error.
- Si cada formato implementa el preceso completo,se duplicara el recorrido y el manejo de errores .Si el proceso instancia un lector concreto directamente,queda ligado a ese formato.La variacion esta en *como se interpreta una linea* , no el flujo de importaciòn.
clase abstarcta se instancia e interfaz nos e instancia

> Un metodo que va acrear una clase que en la implementaicion me dice de que tipo es esta 

Creadora -->Clase Abstracta
Subclase  -->Las q usan el metodo abstracto
Prodcuto --> Lo q el factory method soluciona la clase final 

## Estructura del patrón Factory Method

| Participante | Responsabilidad |
|---|---|
| **Producto** | Interfaz o clase abstracta que define las operaciones disponibles. |
| **Producto concreto** | Implementa las operaciones del producto. |
| **Creador** | Declara el Factory Method y contiene el algoritmo común que utiliza el producto. |
| **Creador concreto** | Sobrescribe el Factory Method para devolver el producto correspondiente. |
| **Cliente** | Selecciona el creador que necesita. |

Cuando Usar 
Un proceso necesita trabajar con diferentes implementaciones de un producto
Se desea conservar un procedimiento comun 

Metodo que va a devolver un prodcuto  - producto generico que las subclases den 

## Abstract Factory
Patron de diseño creacional que define una interfaz paar crear una familia u objetos relacionados  o compatibles, sin que el cliente tenga q conocer sus clases concretas.

Una fabrica concreta proporciona los prodcutos de una variable determinada .El cliente solicita cada prodcuto mediante la interfaz de fabrica y utiliza objetos mediante sus propios contratos.La descicion sobre que familia utilizar  se toma al elegir la fabrica 

-Concentrar la creacion de colaboradores que deben funcionar juntos, de modo que cambiar la familia no obligue a modificar el codiog que lo utiliza 

Solucion 
identiifcar los tipos de prodcuto que colaboran
Definir un contrato para cada tipo de producto
Declarar una intefaz de fabrica de abstarcta de la msima familia 

## Estructura del patrón Abstract Factory

| Participante | Responsabilidad |
|---|---|
| **Fábrica abstracta** | Declara las operaciones para crear los distintos tipos de producto. |
| **Fábrica concreta** | Proporciona instancias de productos que pertenecen a una familia determinada. |
| **Producto abstracto** | Define las operaciones de uno de los tipos de producto (el contrato). |
| **Producto concreto** | Implementa un tipo de producto específico para una familia específica. |
| **Cliente** | Obtiene y utiliza productos exclusivamente mediante abstracciones. |

Cundo usar 
Una funcionalidad depende de varios componentes que deben seleccioanrse juntos
-Existen familias alternativas , como provedores plataformas o protocolos

### Singleton
Es un patron de diseño creacional que restringe una clase a una unica instancia dentro de un ambito definido y proporciona un punto de acceso a esa instancia 
Proposito:
Compartir una configuracion : 
Restringir a una instancia: Impide q los clientes construyan libremente instancias adicionales 
Problema :
Supongamos q varios servicios deben utilizar una misma configuracion predeterminada .Si cada servicio decide crear su propia configuracion o utiliza valores diferentes , el comportamiento de la aplicacion puede divergir .

Compartir una configuracion:crear un objeto al iniciar la aplicacion y entregarlo a los servicios puede ser suficiente.

Restringir una clase o una instancia: La clase debe impedir que los clientes construyan libremente instancias adicionales y  ofrecer acceso a la referencia permitida.

Solucion:
Controlar la creaciond e las instancias del tipo.
Mantener una referencia a la instancia permitida.
Poporcionar un punto de acceso conocido.
Definir el ambito en el q se aplica la unicidad.
Diseñar por separado la mutabilidad y la concurrencia de sus operaciones.

>Enum

Restringe a una clase a una unica instancoa dentro de un ambito definido y proporciona un acceso directo a ella 

| Participante | Responsabilidad |
|---|---|
| **Singleton** | Restringe la instanciación libre y conserva en memoria el objeto compartido. |
| **Punto de acceso** | Medio por el cual los clientes pueden obtener la referencia de la instancia única. |
| **Cliente** | Utiliza las operaciones y el estado del objeto compartido. |
| **Contrato (opcional)** | Interfaz que expresa lo que necesita el cliente, permitiendo usar sustitutos para pruebas. |

```java
public interface Parametros{
        Duracion intervalo();
        String unidad();
} 
public enum Configuracion implement Parametros{

    INSTANCIA;//Punto de acceso unico 

    private final Duracion intervalo = Duration.ofSeconds(30);
    private final String unidad = "C";

    @Override
    public Duracion intervalo(){
        return intervalo
    }
    @Override
    public String unidad(){
        return unidad
    }

}
```

```java
/ SingletonDemo

// Conexion con = Conexion.getInstancia();

public class Conexion {

    private static Conexion instancia;
    private Connection conexion;

    // Constructor privado
    private Conexion() {
        try {
            conexion = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/mi_base",
                "root",
                "1234"
            );
        } catch (SQLException e) {
            throw new RuntimeException(e);
        }
    }

    // Acceso a la única instancia
    public static synchronized Conexion getInstancia() {
        if (instancia == null) {
            instancia = new Conexion(); // USA EL CONSTRUCTOR
        }
        return instancia;
    }
}
```

## Builder 
Organiza la construccion de un objeto mediante pasos separados de su utilizacion
El cliente configura un constructor especializado y obtiene el prodcuto al finalizar el proceso 
Puede ejecutar una secuencia de pasos para obtener representaciones diferentes .
Pasos:
Aislar -> Mantener las opciones de construccion de un objeto separado (Builder)
Configurar -> Exponer operaciones fluidas con nombres que expresen cada decision claramente 
Validar -> Comprobar restricciones y reglas conjuntas de la creacion
Producir -> Construir y devolver el producto final unicamente cuenaod es 100% aceptable

Problema
Supongamos que un objeto necesita datos obligatorios ,opciones y valores predeterminados ç
Constructores gigantes
Setters y estado incompleto 

Solucion
Mantener las opcioens de construccion de un objeto separado 
Exponer operaciones con nombres que exprean cada decicion 
Validar lso datos y restricciones conjuntas
Construir y devolver el prodcuto cuando el estado sea aceptable 

| Rol | Responsabilidad |
|---|---|
| **Producto** | Representa el resultado final construido e inmutable. |
| **Builder (Contrato)** | Define o proporciona las operaciones de configuración y validación. |
| **Builder Concreto** | Mantiene el estado provisional y produce la representación final. |
| **Director (Opcional)** | Coordina una secuencia de construcción repetitiva o reutilizable (recetas). |
| **Cliente** | Elige las opciones, invoca los pasos y solicita el resultado final. |

Cuando usar 
El prodcuto tiene varias opciones o parametros dificiles de distinguir por poscicion 
Se desea aplicar valores predeterminados de forma explicita 
Existen restricciones que dependen de la combinacion de varios datos
El producto no debe quedar disponible mienstras 

Reglas debe tener - >  nombre , intervalo y sensor 

```java
//Builder concreto 
static final class Builder {
    private final String nombre; // Obligatorio en constructor
    private Duration intervalo = Duration.ofSeconds(30); // Predeterminado
    private final List<String> sensores = new ArrayList<>(); // Estado provisional

    Builder(String nombre) {
        this.nombre = Objects.requireNonNull(nombre);
    }

    Builder cada(Duration intervalo) {
        this.intervalo = Objects.requireNonNull(intervalo);
        return this; // Permite interfaz fluida
    }

    PlanMuestreo construir() {
        // Validación estricta final
        if (intervalo.compareTo(Duration.ofSeconds(1)) < 0)
            throw new IllegalArgumentException("Intervalo mínimo: 1s");

        if (sensores.isEmpty())
            throw new IllegalArgumentException("Agrega al menos un sensor");

        return new PlanMuestreo(this); // Barrera superada
    }
}
```

```java
//
// El cliente expresa la configuración de forma legible y fluida
PlanMuestreo.Builder builder = new PlanMuestreo.Builder("Laboratorio")
    .cada(Duration.ofSeconds(10))
    .agregarSensor("S01")
    .agregarSensor("S02");

PlanMuestreo plan = builder.construir();
System.out.println(plan.resumen());
```

## Prototype
Obtiene nuevos objetos a partir de objetod existentes mediante una operacion de copia.El objeto que conoce su estado define como reproducirlo .

```java
// Contrato del prototipo
interface Copiable<T> {
    T copiar();
}

// Componente mutable interno
static final class ReglaUmbral {
    private final String magnitud;
    private double limite; // ¡Estado mutable!

    // Constructor y validadores omitidos...

    // Operación de copia profunda para el componente
    ReglaUmbral copiar() {
        return new ReglaUmbral(magnitud, limite);
    }
}
```
```java
static final class PerfilSensor implements Copiable<PerfilSensor> {
    private String nombre;
    private final List<ReglaUmbral> reglas = new ArrayList<>();

    // ... métodos omitidos ...

    @Override
    public PerfilSensor copiar() {
        // 1. Nueva identidad del contenedor
        PerfilSensor copia = new PerfilSensor(nombre);

        // 2. Copia profunda de los elementos mutables
        // No basta new ArrayList<>(reglas); compartiría instancias
        for (ReglaUmbral regla : reglas) {
            copia.reglas.add(regla.copiar()); // Delegación
        }

        return copia;
    }
}
```



| Pregunta de Diseño Estructural | Patrón Recomendado | El cambio localizado |
|---|---|---|
| ¿Qué implementación específica necesita mi algoritmo general? | Factory Method | Subclase concreta del creador |
| ¿Qué productos deben elegirse juntos para evitar errores? | Abstract Factory | Fábrica del equipo (Familia) |
| ¿Cómo reúno y valido opciones antes de entregar un objeto final? | Builder | Etapas y estado provisional |
| ¿Cómo obtengo una variante independiente de una configuración inicial? | Prototype | Operación de copia profunda |
| ¿Necesito garantizar restrictivamente que exista solo una instancia? | Singleton | Punto de acceso (Ej: Enum) |

