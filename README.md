
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

---

### ¿qué son los patrones de diseño?
Imagínate que estás construyendo una casa. No tienes que inventar desde cero cómo hacer una puerta, instalar una ventana o distribuir las habitaciones. Puedes utilizar soluciones que ya han funcionado en otras casas y adaptarlas a la tuya.

En programación pasa lo mismo.

Un patrón de diseño es una solución que ya se conoce y que podemos reutilizar para resolver un problema frecuente al organizar nuestro código.

No es un código que copias y pegas obligatoriamente. Es una forma de organizar las clases y los objetos.
>¿Para qué sirven?

- Reutilización: aprovechar soluciones que ya funcionan.
- Mantenimiento: hacer que el código sea más fácil de corregir.
- Flexibilidad: poder cambiar una parte sin dañar todo.
- Extensibilidad: agregar nuevas funcionalidades con menos modificaciones.
- Menos acoplamiento: evitar que una clase dependa demasiado de otra clase específica.
Por ejemplo, si tu programa trabaja con sensores y mañana necesitas agregar un sensor nuevo, conviene que puedas hacerlo sin reescribir todo el programa.
2. Los tres tipos de patrones de diseño

> 1. Creacionales

Se encargan de cómo se crean los objetos.

Ejemplos: Factory Method, Abstract Factory, Builder, Prototype y Singleton.


> 2. Estructurales

Organizan cómo se relacionan o conectan las clases y los objetos.

Ejemplos: Adapter, Decorator y Facade.

> 3. De comportamiento

Organizan cómo se comunican los objetos y cómo se reparten las tareas.

Ejemplos: Observer y Strategy.
---
Truco para memorizar:
- Creacionales = crear.
- Estructurales = conectar.
- Comportamiento = comunicarse.
En tu documento, el ejemplo de sensores usa tres patrones: Factory Method crea distintos tipos de sensores, Observer avisa cuando cambia una lectura y Strategy permite cambiar la manera de procesarla.
3. Antes de empezar Java: 5 palabras que debes entender
Si no entiendes estas palabras, los patrones te van a parecer más difíciles de lo que realmente son.
Palabra	Explicación sencilla
Clase	Es el molde para crear objetos.
Objeto	Es algo creado a partir de una clase.
Interfaz	Es un contrato que dice qué acciones debe cumplir una clase.
Instanciar	Crear un objeto a partir de una clase.
Implementar	Escribir el código que cumple lo que exige una interfaz.

Por ejemplo:
class Perro {
    void ladrar() {
        System.out.println("Guau");
    }
}


Aquí, Perro es la clase.
Perro miPerro = new Perro();


Aquí creamos un objeto de la clase Perro.

¿Y qué hace new? Crea un objeto. Si escribes new Perro(), estás creando un perro nuevo en memoria.

Una interfaz sería así:
interface Animal {
    void hacerSonido();
}


La interfaz establece que una clase debe tener el método hacerSonido(). No es el perro todavía: es el contrato que debe cumplir.
### 4. Factory Method: una fábrica que decide qué crear

Imagina que tienes una fábrica que produce sensores. Un día necesitas un sensor de temperatura y otro día uno de humedad.

No quieres que todo tu programa tenga que conocer las clases concretas de cada sensor.

Factory Method permite que una subclase decida qué objeto concreto crear, mientras se conserva un procedimiento general.
Ejemplo sencillo
Imagina que necesitas crear distintos documentos para exportar información: TXT o HTML.

Primero, estableces qué debe hacer cualquier exportador:
```java
interface Exportador {
    void exportar();
}


Ahora creas dos tipos de exportadores:
class ExportadorTXT implements Exportador {
    public void exportar() {
        System.out.println("Exportando a TXT");
    }
}

class ExportadorHTML implements Exportador {
    public void exportar() {
        System.out.println("Exportando a HTML");
    }
}
```


Cada uno cumple el contrato, pero trabaja de manera diferente.

Luego, creas una clase que declara el método de creación:
```java
abstract class Creador {
    abstract Exportador crearExportador();

    void ejecutar() {
        Exportador e = crearExportador();
        e.exportar();
    }
}


Y las subclases deciden qué exportador entregar:
class CreadorTXT extends Creador {
    Exportador crearExportador() {
        return new ExportadorTXT();
    }
}

class CreadorHTML extends Creador {
    Exportador crearExportador() {
        return new ExportadorHTML();
    }
}
```

¿Qué tienes que entender de esto?
- Exportador es el producto.
- ExportadorTXT y ExportadorHTML son los productos concretos.
- Creador es la clase que declara el método de creación y contiene el procedimiento común.
- CreadorTXT y CreadorHTML son los creadores concretos.
- El cliente elige el creador que necesita.

La palabra clave aquí es abstract: la clase declara un método que sus subclases deben implementar. No puedes crear directamente una instancia de una clase abstracta.
¿Cuándo se utiliza Factory Method?
Cuando tienes un procedimiento que debe mantenerse igual, pero necesitas cambiar el tipo de objeto con el que trabaja.

Por ejemplo, importar archivos de distintos proveedores: uno separa los datos con punto y coma y otro con tabulaciones. El proceso general de importar puede ser el mismo, pero cambia la forma de interpretar cada línea.

Frase para el examen: Factory Method permite que las subclases decidan qué producto concreto crear, manteniendo un procedimiento común.

### 5. Abstract Factory: una fábrica que crea una familia completa

Este patrón se parece al anterior, pero tiene una diferencia importante.

Imagina que estás creando una aplicación con dos temas visuales: claro y oscuro.

Cada tema tiene varios componentes:
- Un botón.
- Un menú.
- Una ventana.
Si eliges el tema oscuro, quieres que todos los componentes sean oscuros. No quieres un botón oscuro y un menú claro por accidente.

Abstract Factory crea familias de objetos relacionados que deben funcionar juntos.
Ejemplo en palabras sencillas
Primero, defines los contratos de los productos:
```java
interface Boton {
    void mostrar();
}

interface Menu {
    void mostrar();
}


Después, creas las fábricas que permiten obtener ambos componentes:
interface FabricaUI {
    Boton crearBoton();
    Menu crearMenu();
}
```

Fíjate en algo importante: esta fábrica no crea un solo producto. Tiene dos métodos de creación, uno para el botón y otro para el menú.

Puedes tener una fábrica concreta para el tema oscuro y otra para el tema claro.

Cuando el programa selecciona una fábrica, obtiene los componentes de esa misma familia.

¿Qué tienes que memorizar?
--- 
| Participante | ¿Qué significa? |
|---|---|
| Fábrica abstracta | Declara qué productos se pueden crear. |
| Fábrica concreta | Crea los productos de una familia específica. |
| Producto abstracto | Define qué debe hacer cada tipo de producto. |
| Producto concreto | Es el producto real, como un botón oscuro. |
| Cliente | Utiliza los productos sin depender de sus clases concretas. |

>¿Cuándo se utiliza?
Cuando necesitas varios objetos que deben elegirse juntos porque son compatibles entre sí.

Ejemplos: temas visuales, familias de componentes para diferentes plataformas o productos de distintos proveedores.


 Abstract Factory proporciona una interfaz para crear familias de objetos relacionados sin que el cliente conozca sus clases concretas.

### Diferencia entre Factory Method y Abstract Factory

Factory Method
¿Qué objeto voy a crear?

La subclase decide qué producto concreto crear.

Abstract Factory

¿Qué familia de objetos necesito?

La fábrica elegida crea varios productos relacionados.

 Factory Method = elegir un producto concreto. Abstract Factory = elegir una familia.

### 6. Singleton: una sola instancia

Imagina que tienes un programa que necesita consultar una configuración general. No quieres que cada parte del programa cree su propia configuración y termine usando valores diferentes.

Para eso puedes utilizar Singleton.

Singleton restringe una clase a una única instancia dentro de un ámbito definido y proporciona un punto de acceso para obtenerla.
Ejemplo sencillo en Java
```java
public class Configuracion {

    private static Configuracion instancia;

    private Configuracion() {
    }

    public static synchronized Configuracion getInstancia() {
        if (instancia == null) {
            instancia = new Configuracion();
        }

        return instancia;
    }
}


Vamos por partes.
- private static Configuracion instancia;: guarda la referencia al objeto compartido.
- private Configuracion(): el constructor privado impide que otras clases creen objetos directamente con new Configuracion().
- getInstancia(): es el método público para obtener el objeto.
- if (instancia == null): comprueba si todavía no se ha creado.
- instancia = new Configuracion(): lo crea si aún no existe.
- return instancia: devuelve la instancia existente.
- synchronized: evita que varios hilos ejecuten simultáneamente ese método de forma que creen instancias duplicadas.
Para utilizarlo:
Configuracion c1 = Configuracion.getInstancia();
Configuracion c2 = Configuracion.getInstancia();
```

Ambas variables reciben la misma instancia.
Una forma de recordarlo
Imagina que una universidad tiene una única oficina central de configuración. Todos los departamentos consultan esa misma oficina en lugar de crear una oficina diferente cada uno.
> ¿Cuándo se utiliza?
- Cuando necesitas compartir una instancia.
- Cuando quieres centralizar una configuración.
- Cuando necesitas controlar la creación de un objeto.

 Singleton restringe la creación de instancias y proporciona un punto de acceso a la instancia compartida.

Singleton no significa que solo pueda existir un objeto de cualquier clase en todo el programa. La unicidad se aplica a la clase y al ámbito definidos por su implementación.

### 7. Builder: construir un objeto por pasos

Imagina que quieres construir un informe. Necesitas un nombre, una fecha, un formato, una lista de datos y otras opciones.

Podrías crear un constructor con diez parámetros, pero sería fácil confundirse. También podrías crear el objeto y modificarlo después con muchos setters, dejando un objeto incompleto.

Builder permite construir un objeto paso a paso, configurar sus opciones y validar que todo esté correcto antes de entregarlo.
Ejemplo sencillo
Imagina que necesitas configurar un plan de muestreo para sensores.
```java
PlanMuestreo plan = new PlanMuestreo.Builder("Laboratorio")
    .cada(Duration.ofSeconds(10))
    .agregarSensor("S01")
    .agregarSensor("S02")
    .construir();
```

No te preocupes todavía por conocer todas las clases de este ejemplo. Lo importante es entender qué sucede.
1. Builder("Laboratorio"): establece el nombre obligatorio.
2. .cada(...): configura cada cuánto se toman las muestras.
3. .agregarSensor("S01"): agrega un sensor.
4. .agregarSensor("S02"): agrega otro sensor.
5. .construir(): comprueba los datos y crea el objeto final si todo es válido.


¿Cuándo se utiliza?
Cuando un objeto tiene muchas opciones, valores predeterminados o reglas que deben comprobarse antes de crearlo.

 Builder separa la construcción de un objeto de su utilización y permite configurarlo por etapas antes de producir el resultado final.

### 8. Prototype: copiar un objeto que ya existe
Imagina que tienes un perfil de sensor configurado con:
- Nombre: Sensor de temperatura.
- Límite máximo: 80.
- Límite mínimo: 10.
- Reglas de medición.
Ahora necesitas otro perfil casi igual, pero con un límite máximo de 100.

Puedes crear un objeto desde cero y volver a configurar todo. O puedes copiar el perfil existente y cambiar lo necesario.

Prototype crea nuevos objetos a partir de otros existentes mediante una operación de copia.
```java
Ejemplo sencillo
interface Copiable<T> {
    T copiar();
}


Esta interfaz establece que los objetos que la implementan deben proporcionar un método copiar().

Un perfil podría implementar esa interfaz:
class PerfilSensor implements Copiable<PerfilSensor> {

    private String nombre;

    PerfilSensor(String nombre) {
        this.nombre = nombre;
    }

    @Override
    public PerfilSensor copiar() {
        return new PerfilSensor(nombre);
    }
}
```

Si hacemos esto:
PerfilSensor original = new PerfilSensor("Temperatura");

PerfilSensor copia = original.copiar();


Tenemos dos objetos diferentes con el mismo nombre inicial.

> ¿Cuándo se utiliza?
- Cuando necesitas crear objetos parecidos a uno existente.
- Cuando ya tienes una configuración que deseas reutilizar.
- Cuando copiar el estado resulta más práctico que reconstruirlo desde cero.
Prototype permite crear nuevos objetos copiando instancias existentes, definiendo cómo se reproduce su estado.

### 9. Comparación de los cinco patrones

| Patrón | Pregunta que te debes hacer | Idea clave |
|---|---|---|
| Factory Method | ¿Qué producto concreto debe crear la subclase? | Decidir qué crear. |
| Abstract Factory | ¿Qué conjunto de productos debe funcionar junto? | Crear una familia. |
| Singleton | ¿Cómo controlo que exista una sola instancia? | Una instancia compartida. |
| Builder | ¿Cómo configuro y valido un objeto complejo? | Construir por pasos. |
| Prototype | ¿Cómo creo un objeto parecido a uno existente? | Copiar un objeto. |



>Factory Method
---

Una fábrica decide qué producto fabricar.


>Abstract Factory
---

Una fábrica produce una familia compatible.

>Singleton
---
Una instancia controlada.


>Builder
---

Construir y validar por pasos.


>Prototype
--- 

Copiar una instancia existente.