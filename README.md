# 🌿 GreenBot – Asistente Virtual de Jardinería  
> **Entrega Final** – Generación de Prompts  

![Banner](https://img.shields.io/badge/Entrega-Proyecto%20Final-green)
![JavaScipt](https://img.shields.io/badge/JavaScript-ES2024-yellow)
![IA](https://img.shields.io/badge/IA-Prompt%20Engineering-green)

---

## 📝 Introducción  

**GreenBot** es un asistente virtual diseñado para **automatizar la generación de presupuestos** y la **gestión de la agenda** de un jardinero, utilizando técnicas de **prompt engineering** e **inteligencia artificial**.  

El proyecto busca optimizar la comunicación entre clientes y jardineros, ofreciendo respuestas rápidas, claras y precisas sobre presupuestos, disponibilidad y horarios.

---

## ❗ Presentación del problema  

Los jardineros independientes suelen gestionar de forma **manual** la solicitud de trabajos, los presupuestos y la agenda. Esto trae varios inconvenientes:  

- Demoras en responder a los clientes.  
- Falta de organización en los horarios.  
- Presupuestos inconsistentes o poco claros.  
- Mala experiencia para el cliente.  

**Relevancia del proyecto:**  
Un asistente virtual permite **automatizar** estas tareas, mejorando la **eficiencia**, reduciendo **errores humanos** y brindando **mayor comodidad** tanto para el cliente como para el jardinero.  

---

## 💡 Propuesta de solución  

La solución consiste en desarrollar un **asistente virtual inteligente** que:  

- Reciba **datos del cliente**: nombre, tipo de trabajo, tamaño del terreno y fecha disponible.  
- Genere un **presupuesto estimado** en base al tipo de trabajo y tamaño del área.  
- Verifique la **disponibilidad del jardinero** en la fecha solicitada.  
- Proponga un **horario adecuado** para realizar el trabajo.  
- Devuelva una **respuesta clara, cordial y personalizada**.  

---

## 🤖 Relación con la IA y uso de Prompts  

El proyecto se basa en el uso de **técnicas de prompting** para interactuar con un modelo de **IA generativa**.  

**Prompt Propuesto:** 

Eres un Asistente de Jardinería. Recibirás un mensaje de un cliente con los siguientes datos: 
nombre, dirección, teléfono, problema a resolver, fecha y horario disponible. Genera un presupuesto basado en los siguientes datos:

1) Corte de Cesped

- Corte: $100/m²
- Recolección de restos: $20/m² (opcional)

2) Poda de arbustos

- Pequeños: $5.000
- Medianos: $8.000
- Grandes: $12.000

3) Poda de árboles

- Normales: $30.000
- Grandes (>8m): $45.000
- Palmeras: $10.000
- Recolección de ramas: $15.000 (opcional)

4) Extracción de árboles:

- 2 a 4m: $100.000
- 4 a 8m: $140.000
- 8 a 15m (grúa): $200.000
- más de 15m (grúa): $300.000
- Recolección de ramas: $50.000

Nota: Si se necesita grúa o volquete, agregar el costo extra que cobre la empresa de alquiler.

4.1) Costos adicionales por alquiler:

- Grúa: $250.000 (agregar si el trabajo requiere)
- Volquete: $75.000 (agregar si el cliente lo necesita)

Sabiendo esto deberas generar una salida como la siguiente:

INICIO DE EJEMPLO

Nombre Cliente: [Nombre]  
Dirección: [Dirección]  
Número de teléfono: [Teléfono]  
Fecha Disponible: [DD/MM/AAAA] (hora)  

Tipo de Trabajo: [Descripción con medidas y categoría]  
Presupuesto: [Detalle de costos, incluyendo opcionales]  
Total: [Suma total]

FIN DE EJEMPLO

y deberas dejar un mensaje diciendo que un jardinero se pondra en contacto, como el siguiente:

Un jardinero se pondra en contacto contigo en las proximas 24hs... Saludos!

DATOS A TENER EN CUENTA...

- Trabajamos de lunes a viernes de 8am a 18pm. ten en cuenta la zona horaria de argentina y a partir del dia 22 de septiembre de 2025.
- Solo respondes mensajes sobre estos trabajos, si te piden por otro trabajo, responderas amablemente que no realizamos ese tipo de trabajos.
- y solo respondes preguntas sobre este rubro, ningun otro.

Ahora te dejare un ejemplo de entrada y salida para dejarlo de guia.

***Ejemplo de entrada:*** 

"Hola, me llamo Julian Giansanti, necesito podar un árbol de 10m que bloquea el sol en mi quincho. Vivo en Manuel Belgrano 999, estoy disponible este viernes 12 de septiembre a partir de las 12 del mediodía, mi número es 341-1234-567."

***Ejemplo de salida:***

Nombre Cliente: Julian Giansanti  
Dirección: Manuel Belgrano 999  
Número de teléfono: 341-1234-567  
Fecha Disponible: 12/09/2025 (a partir de las 12:00 hs)  

Tipo de Trabajo: Poda de árbol de 10 metros (Grande)  
Presupuesto: Poda de árbol grande: $45.000 + Recolección (opcional) $15.000  
Total: $60.000

Un jardinero se pondra en contacto contigo en las proximas 24hs... Saludos!

**FIN DE EJEMPLOS**

ahora cuando un cliente deje una nota, genera esa nueva nota: 
{mensajeUsuario}

---


## ✅ Justificación de la viabilidad  

El proyecto es **viable** porque:  

- Los modelos de IA (como Gemini) ya están entrenados, por lo que solo se requiere diseñar buenos prompts.  
- No se necesitan grandes recursos, basta con un entorno de desarrollo local.  
- La agenda del jardinero puede gestionarse inicialmente en **JSON** o una **base de datos ligera**.  
- El prototipo puede construirse en un tiempo razonable utilizando **Python** y librerías simples.  

---

## 🎯 Objetivos  

### **Objetivo general**  
Crear un asistente virtual que automatice presupuestos y gestione la agenda de jardinería.  

### **Objetivos específicos**  
- Diseñar prompts efectivos para interpretar datos del cliente.  
- Calcular presupuestos de manera automática.  
- Verificar disponibilidad del jardinero.  
- Mejorar la experiencia de comunicación con el cliente.  

---

## 🛠️ Metodología
El proyecto se desarrolló siguiendo estas etapas:  
1. **Definición del problema:** Identificación de la dificultad de calcular presupuestos manualmente.  
2. **Diseño del prompt:** Creación de un prompt detallado que contemple los servicios más comunes de jardinería y sus precios.  
3. **Prueba en modelo de IA (Gemini):** Envío de ejemplos de entradas y revisión de las salidas generadas.  
4. **Optimización:** Se agregaron observaciones como el costo de alquiler de grúa ($250.000) y volquete ($75.000).  
5. **Validación:** Comprobación de que el asistente devuelva presupuestos claros y coherentes con los datos ingresados.  

La justificación radica en que esta metodología asegura que el asistente pueda adaptarse a distintos escenarios de clientes reales.  

---

## 🧰 Herramientas y Tecnologías
- **IA Generativa (Gemini / ChatGPT):** para el procesamiento del prompt.  
- **Técnicas de Fast Prompting utilizadas:**  
  - **Few-shot prompting:** incluir ejemplos de entrada/salida para guiar la respuesta del modelo.  
  - **Role prompting:** definición clara del rol (“Eres un Asistente de Jardinería”).  
  - **Instrucciones explícitas:** uso de listas de precios detalladas para reducir ambigüedad.  
  - **Contextual prompting:** integración de observaciones adicionales (grúa, volquete).  

Estas técnicas fueron seleccionadas porque permiten respuestas más precisas, coherentes y cercanas al uso real de un asistente.  


---

## ⚙️ Instalación  y Uso

- Clonar este repositorio:  

   ```bash
   git clone https://github.com/JulianGiansanti7/Generacion-de-Prompts-Entrega2.git


🌐 USO del BOT

Para un apto USO del bot agregar una ApiKey de Google Gemini en main.js

🔗 [ApiKey GEMINI](https://aistudio.google.com/apikey)
