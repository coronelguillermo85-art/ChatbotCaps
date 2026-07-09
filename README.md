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
