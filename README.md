# 🤖 Bot de Triaje para Salud Mental - CAPS

[![Versión](https://img.shields.io/badge/versión-1.0-brightgreen)](https://github.com/coronelguillermo85-art/ChatbotCaps)
[![Estado](https://img.shields.io/badge/estado-funcional-success)](https://github.com/coronelguillermo85-art/ChatbotCaps)
[![Licencia](https://img.shields.io/badge/licencia-MIT-blue)](LICENSE)

Automatización de admisión, priorización y turnos en salud mental para el **CAPS Dr. Bartolomé Giacomotti**.

---

## 📌 Descripción

Bot automatizado para el **Centro de Atención Primaria de la Salud (CAPS) Dr. Bartolomé Giacomotti** (Concepción del Uruguay, Entre Ríos) que realiza **triaje de salud mental**, prioriza pacientes según urgencia y asigna turnos de forma automática.

El bot guía al paciente a través de un cuestionario estructurado, detecta emergencias (ideación suicida, intentos recientes) y, según las respuestas, asigna una prioridad (**ALTA / MEDIA / BAJA**) y un plazo estimado de contacto.

---

## 🚀 Funcionalidades

- ✅ **Triaje automático** con preguntas estructuradas (edad, motivo, tiempo de evolución, riesgo).
- ✅ **Priorización inteligente** (ALTA / MEDIA / BAJA) según el motivo y la urgencia.
- ✅ **Búsqueda de pacientes** por número de teléfono en la base de datos.
- ✅ **Asignación de turnos** (inicial para nuevos pacientes, seguimiento para existentes).
- ✅ **Detección de emergencias** con derivación inmediata al **107**.
- ✅ **Registro automático** en una base externa (GitHub Gist).
- ✅ **Notificación al equipo del CAPS** en casos críticos.
- ✅ **Disponible 24/7** (con despliegue en Railway).

---

## 🛠️ Tecnologías

| Tecnología | Uso |
|------------|-----|
| **n8n** | Automatización del flujo y lógica de negocio |
| **Telegram Bot API** | Interfaz de usuario (prototipo) |
| **WhatsApp Business API** | Canal definitivo (migrable) |
| **GitHub Gist** | Base de datos externa (lectura pública) |
| **Railway** | Hosting en la nube 24/7 |
| **ngrok** | Exposición local para pruebas |

---

## 📱 Comandos del bot

| Comando | Función |
|---------|---------|
| `/start` | Inicia el triaje y asignación de turno |
| `/reset` | Reinicia la sesión del usuario |
| `/help` | Muestra ayuda y contacto de emergencias |

---

## 🖼️ Capturas de pantalla

### Flujo en n8n
![Flujo en n8n](https://github.com/user-attachments/assets/14e90492-9bb1-4988-b2ac-4dd064d5eac9)

### Conversación en Telegram
![Conversación en Telegram](https://github.com/user-attachments/assets/f5f01eae-f862-44cf-834f-4645ffa9c932)

### Base de datos (ejemplo)
![Base de datos](https://github.com/user-attachments/assets/1665f2bb-f31e-4eee-8957-0b4b0cba4ba4)

---

## 🗄️ Base de datos

La base de datos se aloja en un **archivo público de GitHub Gist** con formato CSV separado por `|`.

**Archivo de ejemplo:**  
👉 [pacientes.txt](https://gist.githubusercontent.com/coronelguillermo85-art/61ccc15c981da4105f65e3973f5c41ca/raw/gistfile1.txt)

**Formato:**
```
NOMBRE|TELÉFONO|EDAD|SEXO|MOTIVO|TIEMPO|TRATAMIENTO|PRIORIDAD
Guillermo Coronel|3442123456|37|Masculino|Psiquiatría|más de 3 meses|No|ALTA
```

---

## 🧠 ¿Cómo funciona el bot? (Explicación técnica)

El bot se ejecuta en **n8n** con un flujo de 4 nodos:

1. **Schedule Trigger** – Se activa cada 10 segundos.
2. **Obtener Mensajes** – Consulta la API de Telegram (`/getUpdates`).
3. **Lógica con Gist** – Procesa mensajes, lee la base de datos y genera respuestas (JavaScript).
4. **Enviar Respuesta** – Envía la respuesta al usuario (`/sendMessage`).

**Flujo completo:**
```
Schedule (c/10s) → Obtener Mensajes → Lógica (JS) → Enviar Respuesta → (repite)
```

---

## 📝 Código JavaScript (nodo "Lógica con Gist")

```javascript
const PACIENTES_URL = 'https://gist.githubusercontent.com/coronelguillermo85-art/61ccc15c981da4105f65e3973f5c41ca/raw/gistfile1.txt';

async function leerPacientes() {
    try {
        const res = await fetch(PACIENTES_URL);
        return await res.json();
    } catch(e) { return []; }
}

const updates = $input.item.json.result || [];
if (updates.length === 0) return [];

const state = $getWorkflowStaticData('node');
if (!state.sessions) state.sessions = {};

const outputs = [];

for (const update of updates) {
    const msg = update.message;
    if (!msg || !msg.text) continue;

    const chatId = msg.chat.id;
    const texto = msg.text.trim();
    const userId = String(chatId);

    let session = state.sessions[userId] || { step: 'inicio' };
    let respuesta = '';

    if (texto === '/start') {
        session = { step: 'esperando_telefono' };
        state.sessions[userId] = session;
        respuesta = '🔍 Enviá tu número de teléfono (ej: 3442123456):';
    }
    else if (session.step === 'esperando_telefono') {
        const telefono = texto.replace(/\s/g, '');
        const pacientes = await leerPacientes();
        const encontrado = pacientes.find(p => p.TELÉFONO === telefono);

        if (encontrado) {
            respuesta = `✅ PACIENTE ENCONTRADO\n👤 Nombre: ${encontrado.NOMBRE}\n📞 Teléfono: ${encontrado.TELÉFONO}\n📌 Turno de seguimiento asignado.`;
        } else {
            respuesta = '❌ Número no registrado. Contactá al CAPS.';
        }
        delete state.sessions[userId];
    }
    else {
        respuesta = '📌 Enviá /start para comenzar.';
    }

    if (respuesta) {
        outputs.push({ json: { chatId, message: respuesta } });
    }
}

return outputs;
```

---

## 📦 JSON del flujo (para importar en n8n)

> **Reemplaza `TU_TOKEN_AQUI` por tu token de Telegram.**

```json
{
  "name": "CAPS Bot - Lógica del Triaje",
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
      "parameters": { "jsCode": "const PACIENTES_URL = 'https://gist.githubusercontent.com/coronelguillermo85-art/61ccc15c981da4105f65e3973f5c41ca/raw/gistfile1.txt';\n\nasync function leerPacientes() {\n    try {\n        const res = await fetch(PACIENTES_URL);\n        return await res.json();\n    } catch(e) { return []; }\n}\n\nconst updates = $input.item.json.result || [];\nif (updates.length === 0) return [];\n\nconst state = $getWorkflowStaticData('node');\nif (!state.sessions) state.sessions = {};\n\nconst outputs = [];\n\nfor (const update of updates) {\n    const msg = update.message;\n    if (!msg || !msg.text) continue;\n    \n    const chatId = msg.chat.id;\n    const texto = msg.text.trim();\n    const userId = String(chatId);\n    \n    let session = state.sessions[userId] || { step: 'inicio' };\n    let respuesta = '';\n    \n    if (texto === '/start') {\n        session = { step: 'esperando_telefono' };\n        state.sessions[userId] = session;\n        respuesta = '🔍 Enviá tu número de teléfono (ej: 3442123456):';\n    }\n    else if (session.step === 'esperando_telefono') {\n        const telefono = texto.replace(/\\s/g, '');\n        const pacientes = await leerPacientes();\n        const encontrado = pacientes.find(p => p.TELÉFONO === telefono);\n        \n        if (encontrado) {\n            respuesta = `✅ PACIENTE ENCONTRADO\\n👤 Nombre: ${encontrado.NOMBRE}\\n📞 Teléfono: ${encontrado.TELÉFONO}\\n📌 Turno de seguimiento asignado.`;\n        } else {\n            respuesta = '❌ Número no registrado. Contactá al CAPS.';\n        }\n        delete state.sessions[userId];\n    }\n    else {\n        respuesta = '📌 Enviá /start para comenzar.';\n    }\n    \n    if (respuesta) {\n        outputs.push({ json: { chatId, message: respuesta } });\n    }\n}\n\nreturn outputs;" }
    },
    {
      "name": "Enviar Respuesta",
      "type": "n8n-nodes-base.httpRequest",
      "parameters": { "url": "https://api.telegram.org/botTU_TOKEN_AQUI/sendMessage" }
    }
  ]
}
```

---

## 📋 Priorización automática

| Motivo | Prioridad | Plazo |
|--------|-----------|-------|
| Psiquiatría + ideación/intento | 🚨 **EMERGENCIA** | Derivación al 107 |
| Psiquiatría (sin emergencia) | 🔴 **ALTA** | 24 horas |
| Psicología | 🟡 **MEDIA** | 48 horas |
| Clínica general / Otro | 🟢 **BAJA** | 7 días |

---

## 🔧 Instalación (resumida)

1. **Clonar** este repositorio.
2. **Instalar n8n** (`npm install -g n8n`).
3. **Importar** el JSON en n8n.
4. **Configurar** el token de Telegram (reemplazar `TU_TOKEN_AQUI`).
5. **Activar** el flujo (botón "Active" en verde).
6. **Probar** enviando `/start` al bot.

---

## 📱 Migración a WhatsApp Business

1. Crear app en Meta Developers → obtener `Phone Number ID` y Token.
2. En n8n, reemplazar nodos de Telegram por **Webhook** (entrada) y **HTTP Request** (salida).
3. La lógica JavaScript se mantiene sin cambios.
4. Configurar webhook en Meta: `https://tu-app.railway.app/webhook`.

---

## 🔗 Recursos

- 📂 [Google Drive (documentos)](https://drive.google.com/drive/u/0/folders/1IdkUvw9u_x1RUD6_UMptPTWz_n1MT0kq)
- 🧪 [Bot de prueba en Telegram](https://t.me/Caps_Salud_Mental_Tugip_bot)
- 📄 [Base de datos de ejemplo](https://gist.githubusercontent.com/coronelguillermo85-art/61ccc15c981da4105f65e3973f5c41ca/raw/gistfile1.txt)

---

## 🐞 Errores comunes

| Error | Solución |
|-------|----------|
| `Bad webhook / HTTPS required` | Usar polling o ngrok para localhost. |
| `{"ok":true,"result":[]}` | Cambiar offset a `-1` y enviar mensaje nuevo. |
| `401 Unauthorized` | Token incorrecto. Generar nuevo con `@BotFather`. |
| `Too Many Requests` | Aumentar intervalo del Schedule Trigger a ≥ 10 segundos. |

---

## 👨‍💻 Autor

**Guillermo Coronel** – [GitHub](https://github.com/coronelguillermo85-art)  
Proyecto para el CAPS Dr. Bartolomé Giacomotti

---

## 📞 Emergencias

- 🚨 **107** (gratuito, 24hs)
- 🏥 **Hospital Justo José de Urquiza** – Guardia 24h
- 📍 Concepción del Uruguay, Entre Ríos

---

## 📄 Licencia

MIT – ver archivo [LICENSE](LICENSE).

---

⭐ **¡Si te gusta, dale una estrella!**
