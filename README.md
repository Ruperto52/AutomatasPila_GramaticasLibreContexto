## Información de los Integrantes
* **Institución:** Instituto Politécnico Nacional (IPN)
* **Escuela:** Escuela Superior de Cómputo (ESCOM) 
* **Unidad de Aprendizaje:** Teoría de la Computación 
* **Programa Académico:** Ingeniería en Sistemas Computacionales / Plan 2020 
* **Grupo:** 4CM4
* **Alumnos:** 
   * Diego Ruperto Hernandez (Boleta: 2024630696)
   * Maria Jose Venegas Martinez (Boleta: 2024630831)

---

## Objetivo
El propósito de esta práctica es trabajar con:
* Los autómatas de pila, estructuras de procesamiento más poderosas que los autómatas finitos debido a su capacidad de manejar un espacio de memoria adicional: la pila. Se utilizará la plataforma JFLAP para diseñar e implementar autómatas de pila que procesen lenguajes independientes del contexto y, además, se extenderá el software interactivo desarrollado en prácticas anteriores para incluir simulaciones de autómatas con pila.

* Esta práctica también nos ayudará a definir formalmente los componentes de una gramática independiente del contexto (variables, terminales y reglas de producción) para la construcción de lenguajes específicos. Asimismo, implementar y analizar la simulación del proceso de derivación paso a paso para validar la generación correcta de cadenas válidas dentro del lenguaje, integrando esta lógica de procesamiento en el desarrollo del software interactivo.



## Introduccion 
En esta practica agregamos a nuetra aplicación previamente creada en las practicas de la 2 a la 5, un tema nuevo pero muy relacionado con el tema de la materia: "*Automatas de Pila" estos al igual que los automatas normales nos ayudan con la lectura, aceptación y rechazo de cadenas, lo diferente de los "Automatas de Pila*" es que estos cuentan con una memoria y nos ayudan a aceptar cademas de lenguajes más complejos que los lenguajes de los automatas deterministas y no deterministas. Por otro lado, se incorporan las Gramáticas Libres de Contexto (GLC), las cuales representan un modelo generativo fundamental dentro de la Teoría de la Computación. A diferencia de los autómatas, que actúan como reconocedores o evaluadores de cadenas, las gramáticas nos permiten definir las reglas sintácticas estructurales para generar todas las cadenas válidas de un lenguaje independiente del contexto. Ambos conceptos están estrechamente vinculados, ya que para cada gramática libre de contexto existe un autómata de pila equivalente capaz de reconocer el lenguaje que esta produce.

### Automatas de Pila
Es un tipo de máquina teórica, que recibe una cadena constituida por símbolos de un alfabeto, y determina si esa cadena pertenece al lenguaje que el autómata reconoce.

El autómata se define formalmente como una **7-tupla**:
$$M = (Q, q_0, F, \Sigma, \Gamma, s_0, \Delta)
$$Donde:
* $Q$ es el conjunto (finito) de estados.
* $q_0 \in Q$ es el estado inicial.
* $F$ es el conjunto de estados finales o de aceptación, $\emptyset \neq F \subseteq Q$
* $\Sigma$ es el alfabeto de cinta (alfabeto de entrada).
* $\Gamma$ es el alfabeto de pila.
* $s_0 \in \Gamma$ es el símbolo inicial de pila.
* $\Delta$ es la función de transición del autómata:$$\Delta : Q \times (\Sigma \cup \lambda) \times \Gamma \rightarrow (Q \times \Gamma^*)$$

### Gramaticas libre de contexto
Es un modelo matemático abstracto (un sistema formal de reescritura) que define la sintaxis de un lenguaje mediante un conjunto de reglas que determinan cómo se pueden sustituir y combinar los símbolos para generar cadenas válidas. A diferencia de las gramáticas regulares, sus reglas permiten anidamientos recurrentes y estructuras balanceadas, lo que las vuelve ideales para describir la sintaxis de los lenguajes de programación y el diseño de analizadores sintácticos (parsers).

La gramática se define formalmente como una 4-tupla:
$$G = (V, \Sigma, R, S) $$
Donde:

* **V** es un conjunto finito de variables o símbolos no terminales.

* $\Sigma$ es un conjunto finito de símbolos terminales, mutuamente excluyente con $V$ ($V \cap \Sigma = \emptyset$).

* **R** es un conjunto finito de reglas de producción, donde cada regla mapea una sola variable a una cadena de variables y terminales:

    * $R \subseteq V \times (V \cup \Sigma)^*$ Lo cual comúnmente se escribe de la forma:
        * $A \rightarrow \alpha$, Donde:
         $A \in V$ y $\alpha \in (V \cup \Sigma)^*$.

* **$S \in V$**: es la variable u operador inicial (símbolo de arranque).

El proceso para generar una cadena a partir de la variable inicial aplicando sucesivamente las reglas de producción se conoce como derivación. Si en cada paso se sustituye siempre la variable que está más a la izquierda, se denomina derivación por la izquierda; de manera homóloga, si se sustituye la variable más a la derecha, se denomina derivación por la derecha. Estas secuencias de sustitución pueden representarse de forma jerárquica y visual mediante un árbol de derivación (o árbol sintáctico).

## Funcionalidades del Sistema
La aplicación (desarrollada en Python con Tkinter) implementa los siguientes módulos:

1. **Simulador de Automatas de Pila ```AP``` (Carga)**:
* Permite la carga del automata de Pila desde un formato ```.JFF```.
* Muestra la visualizacion grafica del AP cargado, junto con la 7-tupla que representa como el AP cargado.
* Permite ingresar una cadena para poder ser validada o no.
* Muestra como es la validacion de la cadena ingresada, paso a paso con el recorrido de los estados y la modificacion dentro de la pila. 

2. **Constructor de Automatas de Pila ```AP``` (Construye)**:
* Permite crear un AP apartir de la entrada de cada uno de los elementos de la 7-tupla.
* Muestra la visualizacion grafica del AP contruido, junto con la 7-tupla que representa como el AP.
* Permite ingresar una cadena para poder ser validada o no.
* Muestra como es la validacion de la cadena ingresada, paso a paso con el recorrido de los estados y la modificacion dentro de la pila. 
* Permite guardar el mismo AP que fue contruido dentro de esta ventana con el formato ```.JFF```.

3. **Constructor y Simulador de Gramaticas Libres de Contexto ```GLC```**
* Permite la creacion de una gramatica libre de contexto apartir de las reglas de produccion.
* Carga de la gramatica creada para la consecuente validacion de una cadena, donde se moestrara el recorrido que se usa para poder verificar si es que la cadena sera aceptada o no

## Instalación de entorno virtual
 **Instalación y Configuración de Python:** Antes de comenzar a utilizar **Tkinter** para desarrollar la interfaz gráfica de la práctica, es necesario tener Python instalado y configurado. Para ello, siga los siguientes pasos:

1.**Instalar Python**

* Descargue Python: Visite la página oficial de Python en https://www.python.org/downloads/.
* Instale Python: Ejecute el instalador. Durante la instalación, asegúrese de marcar la casilla **"Add Python to PATH"** para que Python se pueda ejecutar desde cualquier terminal.
* Verifique la Instalación : Una vez instalado, abra una terminal (símbolo del sistema en Windows o terminal en macOS/Linux) y ejecute el siguiente comando:

```
python --version
```

Esto debería mostrar la versión instalada de Python. Para esta aplicacion ocuparemos la version de python 3.12.3

2.**Instalar Visual Studio Code**

Visual Studio Code (VS Code) es un entorno de desarrollo ligero y flexible que puede utilizar para programar en Python.
* Descargue VS Code: Diríjase al sitio oficial de Visual Studio Code y descargue la versión para su sistema operativo.
* Instale la Extensión de Python: Abra **VS Code**, diríjase a la pestaña de **Extensiones** (ícono de cubo en la barra lateral), busque e instale la extensión de **Python**. Esto habilitará herramientas adicionales como el resaltado de sintaxis y depuración para Python.

## Preparación del entorno virtual
1.**Crear un Entorno Virtual en Python**

Es recomendable trabajar en entornos virtuales para mantener las dependencias del proyecto aisladas. A continuación, se explica cómo crear un entorno virtual para su proyecto:
* Abra una terminal en Visual Studio Code.
* Navegue hasta la carpeta de su proyecto o cree una nueva carpeta para su proyecto con:

```
mkdir MiProyecto
cd MiProyecto
```

* Cree un entorno virtual ejecutando el siguiente comando:

```
python -m venv venv
```

Esto creará una carpeta llamada venv que contendrá su entorno virtual.

* Active el entorno virtual :
   * En Windows: ```venv\Scripts\activate```
   * En macOS/Linux: ```source venv/bin/activate```

* Verifique que el entorno está activado: El nombre del entorno (venv) debería aparecer al principio de la línea en su terminal.

2.**Instalar Tkinter**

Con el entorno virtual activado, instale el paquete de Tkinter, que es necesario para desarrollar la interfaz gráfica.
Para ello, ejecute el siguiente comando en la terminal:

   * En Windows: ```pip install tk```
   * En macOS/Linux: ```sudo apt-get install python3-tk   ```

**Probar un Programa Simple en Tkinter**
* Cree un archivo Python: En la carpeta de su proyecto, cree un archivo con el nombre **app.py**.
* Escriba el siguiente código básico en el archivo app.py para probar Tkinter:

 ```python
from tkinter import Tk, Label

app = Tk()
app.title("Hola mundo")
label = Label(app, text="¡Hola, mundo!")
label.pack()
app.mainloop()   
```

* Ejecute el archivo desde la terminal : ```python app.py```

* Verifique que se abre la aplicación: Esto debería abrir una ventana de navegador con el mensaje: **¡Hola Mundo!**

Recomendación
Asegúrese de activar el entorno virtual cada vez que trabaje en su proyecto, para garantizar que las dependencias se instalen correctamente en el entorno aislado.

Una vez listo nuestro compilador, nuestro lenguaje de programacion y las librerias que instalamos dentro de nuestro entorno virtual aislado pasaremos con la funcionalidad de nuestro codigo. 

# Funcionalidad del código

## Funcionamiento dentro del ```pda_logic.py``` (logica de los Automatas de Pila)

### Inicializacion del Automata (```__init__```)
```python
def __init__(self):
    self.states = []
    self.alphabet = set()
    self.stack_alphabet = set()
    self.transitions = []  # Lista de tuplas: (estado_actual, input, pop, estado_sig, push)
    self.initial_state = None
    self.final_states = []
```
* **Qué hace**: Define la estructura de datos interna del Autómata de Pila (AP) basándose en su séxtupla matemática formal $M = (Q, \Sigma, \Gamma, \delta, q_0, Z_0, F)$.
* **Puntos clave**:
    * Define listas y conjuntos (set) para almacenar estados, alfabeto de entrada y alfabeto de la pila evitando duplicados.
    * Inicializa una lista vacía para almacenar las funciones de transición $\delta$ en formato de tuplas estructuradas.
    * Establece las variables de control para identificar el estado inicial único y el conjunto de estados finales de aceptación.

### Importación desde JFLAP (```load_from_jff```)
```python
def load_from_jff(self, filepath):
    tree = ET.parse(filepath)
    root = tree.getroot()
    # ... (Procesamiento de nodos XML de estados y transiciones) ...
```
* **Qué hace**: Lee, analiza y parsea un archivo XML con extensión ```.jff``` generado por o compatible con el software JFLAP, mapeándolo a las variables internas de Python.
* **Puntos clave**:
    * Utiliza la librería nativa ```xml.etree.ElementTree``` para recorrer la estructura del archivo jerárquicamente.
    * Extrae los atributos identificadores (```id```) de los estados y detecta mediante etiquetas hijas <initial> o <final> los roles de cada nodo.
    * Recupera los bloques <transition> transformando las lecturas vacías o nulas de las etiquetas <read>, <pop> y <push> en cadenas vacías ("") que representan el comportamiento lógico de $\lambda$ (lambda).

### Exportación a JFLAP (```save_to_jff```)
```python
def save_to_jff(self, filepath):
    root = ET.Element("structure")
    type_elem = ET.SubElement(root, "type")
    type_elem.text = "pda"
    # ... (Construcción de la estructura XML) ...
```
* **Qué hace**: Toma los datos almacenados en memoria del autómata creado en el Constructor de la aplicación y genera un archivo XML legible y completamente editable por JFLAP.

* **Puntos clave**:
    * Define el encabezado <type>pda</type> obligatorio para que JFLAP reconozca que se trata de un modelo con pila y no un autómata finito regular.

    * Traduce la lista de estados y transiciones de regreso al formato de etiquetas XML estándar (<from>, <to>, <read>, etc.).

    * Escribe físicamente el archivo en el disco usando codificación UTF-8 e insertando la declaración XML reglamentaria.

### Simulación y Validación de Cadenas (```validate_string```)
```python
def validate_string(self, input_string):
    stack = ['Z'] 
    paths = [(input_string, self.initial_state, stack, f"Inicio: q{self.initial_state}, Pila: {stack}")]
    # ... (Bucle de exploración DFS) ...
```
* **Qué hace**: Evalúa de forma interactiva si una cadena es aceptada o rechazada por el autómata de pila, registrando detalladamente el historial de movimientos paso a paso.
* **Puntos clave**:
    * Implementa un algoritmo de Búsqueda en Profundidad (DFS) mediante una pila virtual (paths) para procesar el no-determinismo (múltiples caminos posibles).
    * En cada iteración, evalúa tanto transiciones que consumen símbolos de la cadena como transiciones $\lambda$ (que cambian de estado o modifican la pila sin consumir la entrada).
    * Modifica la pila de manera estricta: realiza un ```.pop()``` si se requiere desapilar un símbolo, e inserta caracteres en orden inverso (reversed) al hacer un Push para que el tope de la pila sea siempre el primer carácter de la regla.
    * Devuelve una bandera booleana (```True/False```) y una traza de texto legible con el comportamiento exacto de la pila y los estados visitados.

### Renderizado Gráfico en Interfaz (```draw_on_canvas```)
```python
def draw_on_canvas(self, canvas):
    canvas.delete("all")
    # ... (Cálculo trigonométrico de posiciones y dibujo de líneas/círculos) ...
```
* **Qué hace**: Se encarga de la representación visual del autómata dentro del componente Canvas de Tkinter, adaptando las dimensiones al tamaño actual de la pantalla.

* **Puntos clave**:
    * Limpia el Canvas por completo al iniciar para evitar superposiciones de gráficos antiguos. 
    * Calcula de manera radial (distribución matemática en círculo usando funciones trigonométricas de seno y coseno) la posición exacta (```x, y```) de cada estado.
    * Agrupa múltiples transiciones que comparten el mismo origen y destino para unirlas en un solo texto separado por saltos de línea, evitando que las flechas se encimen.
    * Utiliza un código de colores estético y funcional: los estados iniciales reciben una flecha indicadora, los estados finales un doble círculo concéntrico con fondo verde, y las transiciones cíclicas (self-loops) se dibujan como óvalos superiores independientes.

## Funcionamiento dentro del ```cfg_logic.py``` (logica de las Gramaticas Libres de Contexto)

### Inicialización de la Gramática (```__init__```)
```python
def __init__(self):
    self.productions = {}
    self.start_symbol = 'S'
```
* **Qué hace**: Define las estructuras de datos esenciales para representar una Gramática Libre de Contexto (GLC) bajo la definición formal del cuarteto matemático $G = (V, \Sigma, R, S)$.
* **Puntos clave**:
    * Crea un diccionario vacío (```self.productions```) destinado a indexar las reglas de sustitución, mapeando cada Variable (No Terminal) con su respectiva lista de cadenas de derivación.
    * Establece de manera predeterminada el carácter ```'S'``` como el Símbolo Inicial de la gramática, el cual será modificado de forma dinámica al procesar la entrada del usuario.

### Carga y Procesamiento de Producciones (```load_from_text```)
```python
def load_from_text(self, text):
    self.productions = {}
    lines = text.strip().split('\n')
    for line in lines:
        if '->' not in line: continue
        head, body = line.split('->')
        head = head.strip()
        # ... (Identificación de símbolo inicial y limpieza de reglas) ...
```
* **Qué hace**: Transforma las reglas de producción que el usuario escribe en formato de texto plano dentro de la interfaz a un modelo asociativo estructurado en memoria.
* **Puntos clave**:
    * Segmenta el texto línea por línea y aísla el lado izquierdo (Cabeza/Variable) del lado derecho (Cuerpo/Reglas de reemplazo) localizando el operador de asignación ->.
    * Asume automáticamente la variable de la primera línea válida procesada como el símbolo inicial de la gramática (```self.start_symbol```).
    * Utiliza el operador de separación | para distinguir las opciones de derivación alternativas de una misma variable.
    * Corrección de robustez: Emplea ```.replace(" ", "")``` para eliminar cualquier espacio en blanco estético introducido por el usuario, evitando que altere la longitud real de los símbolos durante el análisis sintáctico.
    * Traduce las cadenas de texto que representan la palabra vacía (como "e", "ε", o "lambda") en cadenas vacías nativas ("") para representar adecuadamente las transiciones $\epsilon$.

### Simulación de Derivaciones y Validación (```validate_string```)
```python
def validate_string(self, target_string, max_depth=15):
    if not self.productions:
        return False, "No hay producciones cargadas."
    stack = [(self.start_symbol, f"Derivación inicial: {self.start_symbol}", 0)]
    # ... (Algoritmo de búsqueda sintáctica y derivación por la izquierda) ...
```
* **Qué hace**: Determina si una cadena pertenece al lenguaje generado por la gramática libre de contexto, aplicando sustituciones sistemáticas y registrando el árbol o ruta de derivación completo.

* **Puntos clave**:
    * Implementa un algoritmo de análisis sintáctico descendente (Top-Down) modelado mediante una Búsqueda en Profundidad (DFS) auxiliada por una pila interna (```stack```).
    * Forzar una Derivación por la Izquierda (Leftmost Derivation) al examinar secuencialmente la cadena actual y procesar estrictamente la primera variable no terminal encontrada (rompiendo el ciclo interno con un ```break``` tras expandir sus producciones).
    * Incorpora dos mecanismos de control y poda heurística para evitar que el software se cuelgue ante gramáticas con recursividad por la izquierda o bucles infinitos:
    * Límite de profundidad (```depth >= max_depth```): Detiene caminos de derivación excesivamente largos.
    * Filtro de longitud (```len(current_form) > len(target_string) * 2```): Descarta de forma temprana aquellas formas de frase que han crecido demasiado respecto a la cadena objetivo.
    * Retorna un valor lógico (```True/False```) acompañado del historial completo formateado con el operador de derivación =>, listando la regla específica que fue aplicada en cada paso.

## Implementacion dentro del ```main.py```
Este documento describe la arquitectura y los bloques de código añadidos al archivo principal `main.py` para integrar las tres nuevas ventanas de la **Práctica 6**, correspondientes al entorno de Autómatas de Pila (`AP`) y Gramáticas Libres de Contexto (`GLC`).

---

## 1. El Conmutador de Entornos (`Launcher`)

```python
class Launcher:
    def __init__(self, root):
        self.root = root
        # ... (Creación de botones para P1 y P2) ...

    def lanzar_p1(self):
        self.root.destroy()
        # ... (Instancia App - Primer Parcial) ...

    def lanzar_p2(self):
        self.root.destroy()
        new_root = tk.Tk()
        app = AppSegundoParcial(new_root)
        new_root.mainloop()
```

* **Qué hace**: Actúa como el enrutador inicial del sistema, permitiendo al usuario elegir de forma aislada entre el entorno de trabajo del primer parcial o el del segundo parcial.

* **Puntos clave**:
    * Crea una ventana de bienvenida ligera que evita sobrecargar la memoria con interfaces ocultas.
    * Utiliza el método `.destroy()` para cerrar por completo el menú del Launcher antes de abrir el nuevo entorno, previniendo conflictos en el hilo principal de renderizado de Tkinter.
    * Instancia la clase `AppSegundoParcial` entregándole un ciclo de ejecución limpio (`mainloop()`).

### Ventana 1: Simulador de Autómatas de Pila (`Carga JFLAP`)
```python
def setup_tab_pda_sim(self):
    # ... (Botones de carga, Canvas central, campo de validación y consola) ...

def importar_pda(self):
    p = filedialog.askopenfilename(filetypes=[("JFLAP Files", "*.jff")])
    if p:
        self.pda_sim.load_from_jff(p)
        self.pda_sim.draw_on_canvas(self.can_pda_sim)
```
* **Qué hace**: Proporciona la interfaz interactiva para abrir archivos analíticos con extensión `.jff` y ejecutar simulaciones paso a paso de cadenas sobre la pila del autómata.

* **Puntos clave**:
    * Implementa un widget tipo `Canvas` dedicado exclusivamente a renderizar el mapa geométrico del autómata cargado.
    * Vincula el cuadro de diálogo de archivos del sistema operativo (`filedialog.askopenfilename`) para importar el XML estructurado.
    * Envía la cadena de entrada al método de validación y formatea la respuesta mostrando un indicador visual de estado (ACEPTADA en verde / RECHAZADA en rojo) junto al historial completo del comportamiento interno de la pila.

### Ventana 2: Constructor Analítico de Autómatas de Pila
```python
def setup_tab_pda_constructor(self):
    # PANEL IZQUIERDO: Inputs (Q, Σ, Γ, i, F, Transiciones)
    # PANEL DERECHO: Canvas de dibujo y caja de Simulación
    
def upd_and_draw_pda(self):
    # ... (Mapeo de cajas de texto hacia variables de pda_const) ...
    # ... (Procesamiento manual de líneas de transición) ...
    self.pda_const.draw_on_canvas(self.can_pda_c)
```
* **Qué hace**: Recrea una suite de diseño modular dividida en dos columnas para conceptualizar, construir desde cero, graficar en tiempo real y exportar un autómata de pila personalizado.
* **Puntos clave**:
    * Panel de Configuración Estructural: Ofrece campos de entrada de texto independientes para definir de forma explícita cada componente de la séxtupla formal ($Q, \Sigma, \Gamma, q_0, F$).
    * Área de Mapeo de Funciones ($\delta$): Incorpora un editor multilínea (`tk.Text`) optimizado para interpretar cadenas textuales con el formato estandarizado `Origen, Lee, Pop ; Destino, Push`.
    * Interconexión Dinámica: El método `upd_and_draw_pda` procesa las líneas de texto, traduce la convención del símbolo épsilon (interpretando caracteres como `"e"`, `"λ"` o vacíos) y refresca automáticamente el lienzo gráfico.

### Ventana 3: Simulador de Gramáticas Libres de Contexto (LLC)
```python
def setup_tab_cfg(self):
    # ... (Caja de texto de producciones, Entry de cadena, área de derivación) ...

def cargar_gramatica(self):
    texto = self.txt_cfg_prod.get("1.0", tk.END)
    self.cfg_logic.load_from_text(texto)

def evaluar_gramatica(self):
    cadena = self.ent_cfg_cad.get().strip()
    ok, trace = self.cfg_logic.validate_string(cadena)
    # ... (Despliegue del resultado y la traza sintáctica) ...
```
* **Qué hace**: Ofrece un entorno de análisis sintáctico descendente para evaluar la pertenencia de una cadena de caracteres respecto a un conjunto de reglas gramaticales variables.

* **Puntos clave**:
    * Dispone de un área de edición flexible que acepta una sintaxis limpia y convencional utilizando flechas (`->`) y barras de alternancia (`|`).
    * Almacena el estado gramatical en el motor lógico y limpia los canales para procesar la cadena de entrada de manera síncrona.
    * Imprime cronológicamente en una consola especializada el árbol de Derivación por la Izquierda utilizando el símbolo algebraico de transformación `=>`, detallando de forma exacta qué producción fue sustituida en cada paso del recorrido.


## Como ocupar el software
### Primeros pasos
Lo primero que haremos sera como anteriormente lo habiamos explicado crear nuestro entorno virtual,en el cual debemos de verificar que la version de ```python es 3.12.3```, una vez comprobado esta version lo que tenemos que hacer es instalar Tkinter, la version que ocuparemos de Tkinter sera: ```8.6.14``` dentro de nuestro entorno virtual para estar listos para poder ejecutar el programa y asi ver la interfaz grafica.

* Para saber que version tenemos dentro de nuestro entorno virtual desde la linea de comando es: 
  * Saber version de python: ```python3 --version```
  * Saber que version de Tkinter: ```python3 -m tkinter```

Una vez creado nuestro entorno virtual y la libreria de Tkinter estamos listos para ejecutar el comando dentro de la terminal para compilar asi nuestro archivo principal que seria el comando: 

```
python3 main.py
```
