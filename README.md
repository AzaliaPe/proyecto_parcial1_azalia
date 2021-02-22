## Proyecto parcial 1
Este repositorio tiene la finalidad de evidenciar todos los conocimientos adquiridos en el primer parcial de la materia tópicos de física, por lo que se creó un archivo shader que almacena las características de un:
+ Modelo Lambert Wrap
+ Phong
+ Normal Map
+ Normal Strength
+ Rim Light
+ Banded
+ Ramp Texture
### Contenido explicativo
El modelo 3D se obtiene de: https://assetstore.unity.com/
Shader es lo que da color y para crear este archivo es necesario tener una estructura de código con propiedades, un SubShader que contenga Tags, y afuera de esta un CGPROGRAM y ENDCG, en los cuales dentro de ellos se realiza la declaración de variables, estructuras y operaciones para que los efectos deseados sean visibles. 
Se utiliza la directiva #pragma Surface surf CustomLambert para indicar su sombreador de superficie. (CustomLambert es una macro).
Se declara un Albedo: Color sin ninguna alteración, natural, que también sirve para cambiarle el color a la iluminación.
El Lambert Wrap es el más básico y hace uso de un fall off.
+ Falloff: La caída de la sombra y en que magnitud va a ser.
	Llega la luz se esparce hasta que se ve negro.
	Se calcula por medio de la normal, con el producto punto ---> dot, 
	El producto punto entre la normal y la dirección de la luz ---> N dot L
+ Producto punto/escalar (dot): Multiplica el producto de los módulos por el coseno del ángulo.
  			      V1 dot V2 = [Vn * Vn + ....]
			      Ejemplo: V1(1,2,3) * v2(4,5,6) = ((1*4)+(2*5)+(3*6)) = 32°
                                       El resultado es el ángulo de inclinación.
El Phong funciona para crear un efecto de brillo, determina un SpecularColor, SpecularPower, SpecularGloss y GlossSteps. Hace uso del producto punto entre la normal y la dirección de la luz, pero también se crea una variable reflectedLight para obtener una segunda dirección de la luz que sería el reflejo. Ocupa el RdotL y la Specularity.
+ Reflect: Refleja un vector, en este caso se usa reflect para traer la dirección de la luz invertida.
+ RdotL: Reflejo producto punto de viewDir, esto regresa el difuso.
+ viewDir: De donde está viendo el espectador al objeto, se ocupa ya que depende de donde se visualice la luz puede cambiar.
+ Specularity: Es el aspecto visual de los reflejos especulares.
+ SpecularGloss: Que tan amplio es el efecto del brillo.
+ GlossSteps: Lo que hace es agrandar los pasos que le toma al llegar al punto más amplio, también sirve para ahorrar memoria.
+ SpecularColor: Es para el color de la luz del brillo.
+ SpecularPower: Que tan fuerte es el efecto del brillo.
+ Pow:  Devuelve x a la y-ésima potencia de escalares y vectores.
El Normal Map es para agregar una textura, por lo que necesita un MainTex tipo 2D. 
El Normal Strength agrega una textura de normales y requiere de un Normal Texture y un Normal Strength. En el void surf se pone el texColor, normalColor y la normal.
+ Strength: Es para ver la intensidad de la normal.
+ texColor: El color de la textura.
+ normalColor: El color de la normal.
El Rim Light es para que se de un efecto de iluminación solamente en las orillas, contiene un RimColor HDR para mejor definición y un RimPower. En el void surf de agrega el nVwd, para normalizar la dirección por donde se aprecia, el NdotV y el rim para controlar su saturación.
+ RimColor: El color de la iluminación de la orilla.
+ RimPower: La intensidad de la iluminación de la orilla.
+ Normalize: Aquí lo importante es la dirección y si lo pasa a 0 y 1.
+ Saturate: Devuelve el menor número entero no menor que un escalar o cada componente del vector.
+ Emission: Controla la cantidad de color que una superficie emite desde su material.
El banded es para que tenga una iluminación con estilo de anillos entre blanco hasta el negro, necesita de steps tipo rango para controlar la cantidad de veces que se apreciara en el modelo 3D. 
+ lightBandsMultiplier: Decide cuantas bandas va a haber.
+ lightBandsAdditive: Es con el que se le da color o con el que va a sumar más que nada la separación entre las líneas.
+ bandedLightModel: Sirve para ya hacer la operación que mostrará al número de pasos.
+ floor: Redondea al número entero más cercano.
El Ramp Texture es de tipo 2D y es muy similar al banded, solo que en este se le agrega una imagen en escala de grises dependiendo el modelo.
Al final para obtener todos los efectos se crea una variable c.rgb, en donde se multiplican todos los estilos de iluminación.
+ c: color
+ a: alpha
### ¿Cómo clonar?
Para duplicar este proyecto es necesario disponer de:
+ Unity 2020.2.1f1 (64-bit)
+ Visual Studio Code

