📁 **Recursos complementarios del proyecto:** [Carpeta Google Drive - CAPS Bot](https://drive.google.com/drive/u/0/folders/1IdkUvw9u_x1RUD6_UMptPTWz_n1MT0kq)
# 🤖 Bot de Triaje para Salud Mental - CAPS

![Versión](https://img.shields.io/badge/versión-1.0-brightgreen)
![Estado](https://img.shields.io/badge/estado-funcional-success)
![Licencia](https://img.shields.io/badge/licencia-MIT-blue)

## 📌 Descripción

Bot automatizado para el **Centro de Atención Primaria de la Salud (CAPS) Dr. Bartolomé Giacomotti** (Concepción del Uruguay, Entre Ríos) que realiza **triaje de salud mental**, prioriza pacientes según urgencia y asigna turnos de forma automática.

El bot guía al paciente a través de un cuestionario estructurado, detecta emergencias (ideación suicida, intentos recientes) y, según las respuestas, asigna una prioridad (**ALTA / MEDIA / BAJA**) y un plazo estimado de contacto. Todo el proceso es automático y no requiere intervención humana hasta la asignación del turno real.

---

## 🚀 Funcionalidades

- ✅ **Triaje automático** con preguntas estructuradas (edad, motivo, tiempo de evolución, riesgo).
- ✅ **Priorización inteligente** (ALTA / MEDIA / BAJA) según el motivo y la urgencia.
- ✅ **Búsqueda de pacientes** por número de teléfono en la base de datos.
- ✅ **Asignación de turnos** (inicial para nuevos pacientes, seguimiento para existentes).
- ✅ **Detección de emergencias** con derivación inmediata al **107**.
- ✅ **Registro automático** de todas las solicitudes en una base externa (GitHub Gist).
- ✅ **Notificación al equipo del CAPS** en casos críticos (vía email o Telegram interno).
- ✅ **Disponible 24/7** (cuando se despliega en la nube con Railway).

---

## 🛠️ Tecnologías utilizadas

| Tecnología | Uso |
|------------|-----|
| **n8n** | Automatización del flujo de conversación y lógica de negocio. |
| **Telegram Bot API** | Interfaz de usuario (prototipo funcional). |
| **WhatsApp Business API** | Canal definitivo para la producción (migrable). |
| **GitHub Gist** | Base de datos externa (lectura pública) con datos de pacientes. |
| **Railway** | Hosting en la nube para ejecución 24/7 (opcional). |
| **ngrok** | Exposición local para pruebas en desarrollo (opcional). |

---

## 📱 Comandos del bot

| Comando | Función |
|---------|---------|
| `/start` | Inicia el proceso de triaje y asignación de turno. |
| `/reset` | Reinicia la sesión del usuario (borra datos temporales). |
| `/help` | Muestra los comandos disponibles y el número de emergencias (107). |

---

## 🖼️ Capturas de pantalla

### Flujo completo en n8n
![Flujo en n8n](https://github.com/user-attachments/assets/14e90492-9bb1-4988-b2ac-4dd064d5eac9)

### Conversación real con el bot en Telegram
![Conversación en Telegram](https://github.com/user-attachments/assets/f5f01eae-f862-44cf-834f-4645ffa9c932)

### Base de datos de pacientes (ejemplo)
![Base de datos](https://github.com/user-attachments/assets/1665f2bb-f31e-4eee-8957-0b4b0cba4ba4)

---

## 🗄️ Base de datos

La base de datos de pacientes se aloja en un **archivo público de GitHub Gist** con formato CSV separado por pipes (`|`). Esto permite que el bot la lea en tiempo real sin necesidad de autenticación.

**Archivo de ejemplo (datos ficticios):**  
👉 [pacientes.txt - Base de datos del bot](https://gist.githubusercontent.com/coronelguillermo85-art/61ccc15c981da4105f65e3973f5c41ca/raw/gistfile1.txt)

**Formato de cada registro:**

```text
NOMBRE|TELÉFONO|EDAD|SEXO|MOTIVO|TIEMPO|TRATAMIENTO|PRIORIDAD
Guillermo Coronel|3442123456|37|Masculino|Psiquiatría|más de 3 meses|No|ALTA
María López|3442987654|42|Femenino|Psicología|15 días a 3 meses|Sí|MEDIA


