
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

