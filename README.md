# 🤖 Bot de Triaje para Salud Mental - CAPS

## 📌 Descripción
Bot automatizado para el **Centro de Atención Primaria de la Salud (CAPS) Dr. Bartolomé Giacomotti** que realiza triaje de salud mental, prioriza pacientes y asigna turnos.

## 🚀 Funcionalidades
- ✅ Triaje automático con preguntas estructuradas
- ✅ Priorización ALTA/MEDIA/BAJA según riesgo
- ✅ Búsqueda de pacientes por teléfono
- ✅ Asignación de turnos (inicial o seguimiento)
- ✅ Detección de emergencias (derivación al 107)

## 🛠️ Tecnologías
| Tecnología | Uso |
|------------|-----|
| n8n | Automatización del flujo de conversación |
| Telegram Bot API | Interfaz con el usuario |
| GitHub Gist | Base de datos externa (lectura pública) |
| ngrok | Exposición local para pruebas (opcional) |

## 📱 Comandos del bot
| Comando | Función |
|---------|---------|
| `/start` | Iniciar triaje |
| `/reset` | Reiniciar sesión |
| `/help` | Mostrar ayuda |

## 🖼️ Capturas de pantalla
## 📄 Código del flujo (n8n)

El flujo exportado desde n8n tiene esta estructura principal:

```json
{
  "name": "CAPS Bot - Con Gist",
  "nodes": [
    {
      "name": "Schedule Trigger",
      "type": "n8n-nodes-base.scheduleTrigger",
      "parameters": { "rule": { "interval": [{ "field": "seconds", "secondsInterval": 10 }] } }
    },
    {
      "name": "Obtener Mensajes",
      "type": "n8n-nodes-base.httpRequest",
      "parameters": { "url": "https://api.telegram.org/botTU_TOKEN_AQUI/getUpdates" }
    },
    {
      "name": "Lógica con Gist",
      "type": "n8n-nodes-base.code",
      "parameters": { "jsCode": "// Lógica completa del bot" }
    },
    {
      "name": "Enviar Respuesta",
      "type": "n8n-nodes-base.httpRequest", 
      "parameters": { "url": "https://api.telegram.org/botTU_TOKEN_AQUI/sendMessage" }
    }
  ]
}
```

> ⚠️ **Nota:** El token aparece como `TU_TOKEN_AQUI`. Reemplazalo por tu propio token de Telegram.
### Flujo en n8n
<img width="1342" height="925" alt="image" src="https://github.com/user-attachments/assets/ec0569a2-a110-4ce1-8cef-66257e9ebfb9" />


### Conversación en Telegram
<img width="310" height="649" alt="image" src="https://github.com/user-attachments/assets/37dc86ff-9cc5-4069-ae59-02fb075fea38" />


## 🗄️ Base de datos

La base de datos de pacientes se aloja en un **archivo público de GitHub Gist** para que el bot pueda leerla en tiempo real.

**Base de ejemplo (datos ficticios):**
👉 [pacientes.txt - Base de datos del bot](https://gist.githubusercontent.com/coronelguillermo85-art/61ccc15c981da4105f65e3973f5c41ca/raw/gistfile1.txt)

**Formato de cada registro (CSV con separador `|`):**
```text
NOMBRE|TELÉFONO|EDAD|SEXO|MOTIVO|TIEMPO|TRATAMIENTO|PRIORIDAD
Ejemplo|3442123456|37|Masculino|Psiquiatría|más de 3 meses|No|ALTA
