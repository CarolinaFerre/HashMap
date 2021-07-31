# ejercicios_HashMap
Colecciones HashMap


MAPS. CLASES UTILIZADAS
_______________________


VENTAJAS:
_________
.Asociación Clave
-No claves iguales

INCONVENIENTES:
_______________
.Poca eficiencia comparado con las demás colecciones

TIPOS:
______
HashMap
LinkedHashMap
TreeMap
EnumMap
WeakHashMap
HashTable
ConcurrentHashMap


HASHMAP:
________
No permite la ordenación
Es más eficiente que las demás

FUNCIONAMIENTO MAP <K,V>
________________________

K-->CLAVE
V-->VALOR


Ejemplo:

clave   valor
_____________
1       Valor1
2       Valor2
3       Valor3


Tenemos una clave y un valor, un valor tiene que ser identificado con una clase. Ejemplo si registro un empleado este debe de ser 
identificado con una clave determinada.

La clave no tiene por qué ser un número, son genéricos porque la clase puede ser cualquier objeto y como valor tambén.

La clase hashMap tiene muchos métodos pero los fundamentales son los siguientes:

Método put -->put(K,V)-->permite almacenar elementos dentro de la colección, para ello hace falta la clave del elemento y el elemento.

Método get --> V get(Object key-->me pide por parámetro una clave que es un objeto en realidad, me devuelve el valor correspondiente de esa clave.

Método set--> Set <Map.Entry <K,V> entrySet() --> Nos pide un genérico que es una interfaz interna, y la interfaz Map.Entry es una interfaz interna 
que pertenece a la interfaz Map y esta interfaz también crea genéricos como la clave y el valor. Devuele un set de los elementos de tipo map que hay en este set.

public Set<Map.Entry<K,V>> entrySet(): Obtiene la colección (colección de conjuntos) de todos los objetos de pares clave-valor en la colección de mapas.
es devolver una colección. La colección almacena objetos. La clase de creación de objetos tiene dos atributos, a saber, clave y valor.Par clave-valor。
donde Entry es una clase interna estática que pertenece a Map. Al crear un objeto Map, se creará un objeto Entry al mismo tiempo para registrar la relación de mapeo entre claves y valores.

for(Map.Entry <String,Empleado> personaEmpleado: listaEmpleados.entrySet()){
        
        String clave=personaEmpleado.getKey();
        
        Empleado valor=personaEmpleado.getValue();
        
        System.out.println("Clave= "+clave +" Valor= " +valor);
        
   
      }
      
 
 Métodos en la clase Entry:
 

equals(Object o)
getKey()
getValue()
hashCode()
setValue()


import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Set;

public class MapBlogTest {

    public static void main(String[] args) {
    
        // Crea un objeto HashMap
        
        HashMap<String, String> map=new HashMap<>();
        
        map.put("Clave 1", "Valor 1");
        
        map.put("Llave 2", "Valor 2");
        
        map.put("Llave 3", "Valor 3");

        // Obtener una colección de objetos
        
        Set<Map.Entry<String, String>> entries=map.entrySet();

        // Uso mejorado para recorrido
        
        for (Map.Entry<String, String> s : entries) {
        
            // ①Puedes generar directamente s para obtener pares clave-valor
            
            System.out.println(s);

            // ②También puede usar el método de la clase Entry para sacar la clave y el valor por separado
            
            String key=s.getKey();        //Obtener la clave
            
            String value=s.getValue();    // Obtener valor
            
            System.out.println(key + "=" + value);    // Valor de la clave de salida
        }

        // Usa while para recorrer con el iterador en la colección
        
        Iterator<Map.Entry<String, String>> it=entries.iterator();
        
        while (it.hasNext()) {
        
            Map.Entry<String, String> next=it.next();
            
            System.out.println(next);

            String key=next.getKey();        //Obtener la clave
            
            String value=next.getValue();    // Obtener valor
            
            System.out.println(key + "=" + value);    // Valor de la clave de salida
        }

    }
}
  
  
  
  
  
Método remove--> remove(Object key) --> permite borrar un elemento del mapa

Ejemplo: 

import java.util.HashMap;

public class UsoMapas {

    public static void main(String[]args){
    
    HashMap <String,Empleado> listaEmpleados=new HashMap<String,Empleado>();
    //String sería la clave y Empleado el valor
    
      listaEmpleados.put("100",new Empleado("Juan"));
      //Almacenamos en el mapa clave 100 y empleado Juan
      listaEmpleados.put("101",new Empleado("Antonio"));
      listaEmpleados.put("102",new Empleado("Maria"));
      listaEmpleados.put("103",new Empleado("Lucia"));
      
      System.out.print(listaEmpleados);
      
      listaEmpleados.remove("101");
      //Me elimina a Antonio
      
      System.out.println(listaEmpleados);
      
      listaEmpleados.put("103", new Empleado("Ana"));
      //Sobreescribe los datos del objeto que ya estaba creado, sustituye Lucía por Ana
      
      
     for(Map.Entry <String,Empleado> personaEmpleado: listaEmpleados.entrySet()){
        String clave=personaEmpleado.getKey();
        
        Empleado valor=personaEmpleado.getValue();
        
        System.out.println("Clave= "+clave +" Valor= " +valor);
        
   
      }
    }

class Empleado{
  
  public Empleado(String nombre){
  this.nombre=nombre;
  salario=2000;
  }
  
  
  @Override
  public String toString(){
    return "Empleado [nombre=" +nombre+", salario= "+salario+"]";
    
    
   private String nombre;
   private double salario;
   
