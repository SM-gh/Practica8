## Universidad Nacional Autónoma de México
### Facultad de Ingeniería
#### Técnicas de Programación - Ingeniería Mecatrónica

##### *Colecciones*

*No de práctica: 8*

1. *Objetivos de aprendizaje* 
 
I. Objetivos generales:  Entender el uso, creación y manejo de las colecciones. 
 
 
II. Objetivos específicos:
* Entender el funcionamiento de las colecciones.
* Aprender a crear colecciones.
* Aprender los métodos para trabajar con colecciones.
 
2. *Introducción*

Una colección es un contenedor que alberga un grupo de objetos, que igualmente, proporciona un conjunto de métodos estándar para enumerar, comparar y crear tales objetos.

Los objetos que pueden guardarse en una colección deber pertenecer todos a una misma clase o bien a una clase y sus subclases.

Las colecciones tienen diferentes métodos para realizar tareas, de las más comunes son:
* Agregar un elemento.
* Insertar un elemento en determinada posición de la colección.
* Eliminar un elemento en cierta posición.

Agregando a la versatilidad de poder modificar su tamaño y desplazar datos, las colecciones
pueden contener, enteros, flotantes, strings y objetos.

3. *Desarrollo*
 
I. Actividad 1

*Implementación de una colección*
 
El alumno utilizará una estructura de colección para generar registros de algún tipo de objeto utilizando al menos 3 operaciones fundamentales para el manejo de la colección.

II. Actividad 2

*Operaciones con los colecciones*
 
El alumno realizará operaciones con objetos (clases creadas por ellos)almacenados en al menos dos colecciones, utilizando para ello las estructuras de control más adecuadas.
 
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace Práctica8
{
    static class Program
    {
        /// <summary>
        /// Punto de entrada principal para la aplicación.
        /// </summary>
        [STAThread]
        static void Main()
        {
            Application.EnableVisualStyles();
            Application.SetCompatibleTextRenderingDefault(false);
            Application.Run(new Form1());
        }
    }
}

```
--- 

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Práctica8
{
    class Computadora
    {
        private string color;
        private string marca;
        private byte cantidad;
        private float precio;

        public string Marca
        {
            get
            {
                return marca;
            }
            set
            {
                if (value == "")
                {
                    marca = "HP";
                }
                else
                {
                    marca = value;
                }
            }
        }
        
        public string Color
        {
            get
            {
                return color;
            }
            set
            {
                if (value == "morado")
                {
                    color = "negro";
                }
                else
                {
                    color = value;
                }
            }
        }
       
        public float Precio
        {
            get
            {
                return precio;
            }
            set
            {
                if (value <= 0)
                {
                    precio = 10000;
                }
                else
                {
                    precio = value;
                }
            }
        }
       
        public byte Cantidad
        {
            get
            {
                return cantidad;
            }
            set
            {
                if (value <= 0 && value >= 9)
                {
                    cantidad = 1;
                }
                else
                {
                    cantidad = value;
                }
            }
        }
       
        public Computadora(string Color, string Marca, byte Cantidad, float Precio)
        {
            this.Color = Color;
            this.Marca = Marca;
            this.Cantidad = Cantidad;
            this.Precio = Precio;

        }

        }
}

```
---

```
using System.Collections;
using System.Drawing;
using System.Windows.Forms;

namespace Práctica8
{
    public partial class Form1 : Form
    {
        ArrayList dispositivos;
        ArrayList CostoTotal;
        private int i=0;
        private float suma = 0;
        public Form1()
        {
            dispositivos = new ArrayList();
            CostoTotal = new ArrayList();
            InitializeComponent();
        }

        private void button1_Click(object sender, System.EventArgs e)
        {
            dispositivos.Add(new Computadora(txtbMarca.Text, txtbColor.Text, byte.Parse(txtbCantidad.Text), float.Parse(txtbPrecio.Text)));
            CostoTotal.Add(float.Parse(txtbPrecio.Text));
            Computadora miComputadora = (Computadora)dispositivos[i++]; //Se hace un casteo
            MessageBox.Show("Se almacenó correctamente.");
            txtbMarca.Clear();
            txtbColor.Clear();
            txtbCantidad.Clear();
            txtbPrecio.Clear();
        }

        private void button2_Click(object sender, System.EventArgs e)
        {
            if (i == dispositivos.Count) 
            {
                i = 0;
            }
            if (i < dispositivos.Count)
            {
                Computadora miComputadora = (Computadora)dispositivos[i++];
                txtbMarca.Text = miComputadora.Marca;
                txtbColor.Text = miComputadora.Color;
                txtbCantidad.Text = miComputadora.Cantidad.ToString();
                txtbPrecio.Text = miComputadora.Precio.ToString();
            }
            
        }

        private void btnCostoTotal_Click(object sender, System.EventArgs e)
        {
            for (i = 0; i < CostoTotal.Count; i++)
            {
                suma +=  float.Parse(CostoTotal[i].ToString());
            }
            lbCostoTotal.Visible = true;
            lbCostoTotal.Text = suma.ToString();
        }
    }
}


```
---
 
6. Bibliografía  
 
* CEBALLOS SIERRA, Francisco Javier. Microsoft C#. Curso de programación. México, Alfaomega, 2007   
* DEITEL, Harvey y Deitel, PAUL. C# Cómo programar. España, Pearson, 2007   
* LÓPEZ ROMÁN, Leobardo. Metodología de la programación orientada a objetos. México, Alfaomega, 2007
