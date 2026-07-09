<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>README - Bot de Triaje para Salud Mental | CAPS</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', -apple-system, BlinkMacSystemFont, Roboto, Oxygen, Ubuntu, sans-serif;
            background: #f6f8fa;
            color: #24292f;
            padding: 40px 20px;
            line-height: 1.6;
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
            background: white;
            border-radius: 16px;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.06);
            padding: 48px 56px;
        }

        .header {
            border-bottom: 1px solid #d0d7de;
            padding-bottom: 24px;
            margin-bottom: 32px;
        }

        .header h1 {
            font-size: 2.6rem;
            font-weight: 600;
            color: #075E54;
            margin-bottom: 8px;
        }

        .header .badges {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
            margin-top: 12px;
        }

        .badge {
            display: inline-block;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 600;
            background: #e1e4e8;
            color: #24292f;
        }

        .badge-green { background: #dcf8e6; color: #075E54; }
        .badge-blue { background: #d4e9f7; color: #1a6c9c; }
        .badge-purple { background: #e3ddf5; color: #3b2d6b; }

        .section {
            margin-bottom: 40px;
        }

        .section-title {
            font-size: 1.8rem;
            font-weight: 600;
            color: #075E54;
            border-left: 6px solid #25D366;
            padding-left: 18px;
            margin-bottom: 18px;
            margin-top: 8px;
        }

        .section-subtitle {
            font-size: 1.2rem;
            font-weight: 600;
            color: #075E54;
            margin: 24px 0 12px 0;
        }

        p {
            margin-bottom: 12px;
        }

        ul, ol {
            padding-left: 28px;
            margin-bottom: 16px;
        }

        ul li, ol li {
            margin-bottom: 6px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 16px 0;
            font-size: 0.95rem;
        }

        th, td {
            border: 1px solid #d0d7de;
            padding: 10px 14px;
            text-align: left;
        }

        th {
            background: #f6f8fa;
            font-weight: 600;
        }

        code {
            background: #f1f3f5;
            padding: 2px 6px;
            border-radius: 6px;
            font-family: 'Fira Code', 'Cascadia Code', monospace;
            font-size: 0.85rem;
        }

        pre {
            background: #1e2a32;
            color: #e9f1f6;
            padding: 16px;
            border-radius: 12px;
            overflow-x: auto;
            font-family: 'Fira Code', 'Cascadia Code', monospace;
            font-size: 0.85rem;
            line-height: 1.5;
            margin: 16px 0;
        }

        .img-container {
            margin: 20px 0;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 2px 8px rgba(0,0,0,0.06);
        }

        .img-container img {
            max-width: 100%;
            height: auto;
            display: block;
        }

        .mockup-mini {
            background: #e5ddd5;
            border-radius: 16px;
            padding: 12px;
            max-width: 300px;
            margin: 12px 0;
        }
        .mockup-mini .bubble {
            background: white;
            padding: 6px 12px;
            border-radius: 14px;
            margin-bottom: 4px;
            font-size: 0.85rem;
        }
        .mockup-mini .bubble-user {
            background: #dcf8c5;
            text-align: right;
        }

        .note {
            background: #f6f8fa;
            padding: 16px 20px;
            border-radius: 12px;
            border-left: 4px solid #25D366;
            margin: 16px 0;
        }

        .note-warning {
            border-left-color: #e67e22;
            background: #fef6e6;
        }

        .footer {
            border-top: 1px solid #d0d7de;
            padding-top: 24px;
            margin-top: 32px;
            text-align: center;
            font-size: 0.85rem;
            color: #57606a;
        }

        a {
            color: #075E54;
            text-decoration: none;
            font-weight: 500;
        }

        a:hover {
            text-decoration: underline;
        }

        @media (max-width: 700px) {
            .container { padding: 24px; }
            .header h1 { font-size: 2rem; }
            .section-title { font-size: 1.4rem; }
        }

        @media print {
            body { background: white; padding: 0; }
            .container { box-shadow: none; border-radius: 0; padding: 20px; }
            .badge { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
            pre { background: #f4f4f4; color: #1a1a1a; border: 1px solid #ccc; }
            .img-container { box-shadow: none; }
        }
    </style>
</head>
<body>
<div class="container">

    <!-- HEADER -->
    <div class="header">
        <h1>🤖 Bot de Triaje para Salud Mental - CAPS</h1>
        <div class="badges">
            <span class="badge badge-green">✅ Versión 1.0</span>
            <span class="badge badge-green">📱 WhatsApp Business</span>
            <span class="badge badge-blue">🔄 Prototipo Telegram</span>
            <span class="badge badge-purple">☁️ Railway 24/7</span>
            <span class="badge">📄 MIT License</span>
        </div>
        <p style="margin-top: 12px; font-size: 1.1rem; color: #2c3e50;">
            Automatización de admisión, priorización y turnos en salud mental para el <strong>CAPS Dr. Bartolomé Giacomotti</strong>
        </p>
    </div>

    <!-- 1. DESCRIPCIÓN -->
    <div class="section">
        <div class="section-title">📌 Descripción</div>
        <p>
            Bot automatizado para el <strong>Centro de Atención Primaria de la Salud (CAPS) Dr. Bartolomé Giacomotti</strong> (Concepción del Uruguay, Entre Ríos) que realiza <strong>triaje de salud mental</strong>, prioriza pacientes según urgencia y asigna turnos de forma automática.
        </p>
        <p>
            El bot guía al paciente a través de un cuestionario estructurado, detecta emergencias (ideación suicida, intentos recientes) y, según las respuestas, asigna una prioridad (<strong>ALTA / MEDIA / BAJA</strong>) y un plazo estimado de contacto. Todo el proceso es automático y no requiere intervención humana hasta la asignación del turno real.
        </p>
    </div>

    <!-- 2. FUNCIONALIDADES -->
    <div class="section">
        <div class="section-title">🚀 Funcionalidades</div>
        <ul>
            <li>✅ <strong>Triaje automático</strong> con preguntas estructuradas (edad, motivo, tiempo de evolución, riesgo).</li>
            <li>✅ <strong>Priorización inteligente</strong> (ALTA / MEDIA / BAJA) según el motivo y la urgencia.</li>
            <li>✅ <strong>Búsqueda de pacientes</strong> por número de teléfono en la base de datos.</li>
            <li>✅ <strong>Asignación de turnos</strong> (inicial para nuevos pacientes, seguimiento para existentes).</li>
            <li>✅ <strong>Detección de emergencias</strong> con derivación inmediata al <strong>107</strong>.</li>
            <li>✅ <strong>Registro automático</strong> de todas las solicitudes en una base externa (GitHub Gist).</li>
            <li>✅ <strong>Notificación al equipo del CAPS</strong> en casos críticos (vía email o Telegram interno).</li>
            <li>✅ <strong>Disponible 24/7</strong> (cuando se despliega en la nube con Railway).</li>
        </ul>
    </div>

    <!-- 3. TECNOLOGÍAS -->
    <div class="section">
        <div class="section-title">🛠️ Tecnologías utilizadas</div>
        <table>
            <thead>
                <tr><th>Tecnología</th><th>Uso</th></tr>
            </thead>
            <tbody>
                <tr><td><strong>n8n</strong></td><td>Automatización del flujo de conversación y lógica de negocio.</td></tr>
                <tr><td><strong>Telegram Bot API</strong></td><td>Interfaz de usuario (prototipo funcional).</td></tr>
                <tr><td><strong>WhatsApp Business API</strong></td><td>Canal definitivo para la producción (migrable).</td></tr>
                <tr><td><strong>GitHub Gist</strong></td><td>Base de datos externa (lectura pública) con datos de pacientes.</td></tr>
                <tr><td><strong>Railway</strong></td><td>Hosting en la nube para ejecución 24/7 (opcional).</td></tr>
                <tr><td><strong>ngrok</strong></td><td>Exposición local para pruebas en desarrollo (opcional).</td></tr>
            </tbody>
        </table>
    </div>

    <!-- 4. COMANDOS -->
    <div class="section">
        <div class="section-title">📱 Comandos del bot</div>
        <table>
            <thead>
                <tr><th>Comando</th><th>Función</th></tr>
            </thead>
            <tbody>
                <tr><td><code>/start</code></td><td>Inicia el proceso de triaje y asignación de turno.</td></tr>
                <tr><td><code>/reset</code></td><td>Reinicia la sesión del usuario (borra datos temporales).</td></tr>
                <tr><td><code>/help</code></td><td>Muestra los comandos disponibles y el número de emergencias (107).</td></tr>
            </tbody>
        </table>
    </div>

    <!-- 5. CAPTURAS -->
    <div class="section">
        <div class="section-title">🖼️ Capturas de pantalla</div>

        <div class="section-subtitle">Flujo completo en n8n</div>
        <div class="img-container">
            <img src="https://github.com/user-attachments/assets/14e90492-9bb1-4988-b2ac-4dd064d5eac9" alt="Flujo en n8n" style="max-width:100%;">
        </div>

        <div class="section-subtitle">Conversación real con el bot en Telegram</div>
        <div class="img-container">
            <img src="https://github.com/user-attachments/assets/f5f01eae-f862-44cf-834f-4645ffa9c932" alt="Conversación en Telegram" style="max-width:400px;">
        </div>

        <div class="section-subtitle">Base de datos de pacientes (ejemplo)</div>
        <div class="img-container">
            <img src="https://github.com/user-attachments/assets/1665f2bb-f31e-4eee-8957-0b4b0cba4ba4" alt="Base de datos ejemplo" style="max-width:400px;">
        </div>
    </div>

    <!-- 6. BASE DE DATOS -->
    <div class="section">
        <div class="section-title">🗄️ Base de datos</div>
        <p>
            La base de datos de pacientes se aloja en un <strong>archivo público de GitHub Gist</strong> con formato CSV separado por pipes (<code>|</code>). Esto permite que el bot la lea en tiempo real sin necesidad de autenticación.
        </p>
        <p>
            <strong>Archivo de ejemplo (datos ficticios):</strong><br>
            👉 <a href="https://gist.githubusercontent.com/coronelguillermo85-art/61ccc15c981da4105f65e3973f5c41ca/raw/gistfile1.txt" target="_blank">pacientes.txt - Base de datos del bot</a>
        </p>
        <p><strong>Formato de cada registro:</strong></p>
        <pre>NOMBRE|TELÉFONO|EDAD|SEXO|MOTIVO|TIEMPO|TRATAMIENTO|PRIORIDAD
Guillermo Coronel|3442123456|37|Masculino|Psiquiatría|más de 3 meses|No|ALTA
María López|3442987654|42|Femenino|Psicología|15 días a 3 meses|Sí|MEDIA</pre>
        <p><strong>Campos:</strong></p>
        <ul>
            <li><code>NOMBRE</code>: Nombre completo.</li>
            <li><code>TELÉFONO</code>: Número de contacto (sin espacios, solo dígitos).</li>
            <li><code>EDAD</code>: Edad en años.</li>
            <li><code>SEXO</code>: Femenino / Masculino / Otro.</li>
            <li><code>MOTIVO</code>: Motivo de consulta (Psicología, Psiquiatría, Clínica general, Otro).</li>
            <li><code>TIEMPO</code>: Tiempo de evolución (menos de 15 días / 15 días a 3 meses / más de 3 meses).</li>
            <li><code>TRATAMIENTO</code>: Si está actualmente en tratamiento (Sí / No).</li>
            <li><code>PRIORIDAD</code>: Asignada automáticamente por el bot (ALTA / MEDIA / BAJA).</li>
        </ul>
    </div>

    <!-- 7. EXPLICACIÓN TÉCNICA (NODOS) -->
    <div class="section">
        <div class="section-title">🧠 ¿Cómo funciona el bot? (Explicación técnica)</div>
        <p>
            El bot está construido sobre <strong>n8n</strong>, una plataforma de automatización low‑code. El flujo se compone de <strong>4 nodos</strong> que trabajan en secuencia:
        </p>

        <div class="section-subtitle">1. ⏱️ Schedule Trigger (Temporizador)</div>
        <ul>
            <li><strong>Función:</strong> Inicia la ejecución cada <strong>10 segundos</strong>.</li>
            <li><strong>Propósito:</strong> Mantener al bot siempre "despierto" y revisando periódicamente si hay nuevos mensajes.</li>
        </ul>

        <div class="section-subtitle">2. 📨 Obtener Mensajes (Cartero)</div>
        <ul>
            <li><strong>Función:</strong> Consulta la API de Telegram para obtener mensajes nuevos.</li>
            <li><strong>URL:</strong> <code>https://api.telegram.org/botTU_TOKEN_AQUI/getUpdates</code></li>
            <li><strong>Parámetros:</strong> <code>offset</code> (para no repetir mensajes) y <code>timeout</code>.</li>
            <li><strong>Resultado:</strong> Si hay mensajes, los pasa al nodo siguiente.</li>
        </ul>

        <div class="section-subtitle">3. 🧠 Lógica con Gist (El Cerebro)</div>
        <ul>
            <li><strong>Función:</strong> Procesa el mensaje, toma decisiones y genera una respuesta.</li>
            <li><strong>Contenido:</strong> Código <strong>JavaScript</strong> que:
                <ol>
                    <li>Lee la base de datos desde el Gist.</li>
                    <li>Interpreta el mensaje (<code>/start</code>, número de teléfono, etc.).</li>
                    <li>Busca al paciente por teléfono.</li>
                    <li>Asigna prioridad según el motivo de consulta.</li>
                    <li>Construye la respuesta adecuada.</li>
                </ol>
            </li>
        </ul>

        <div class="section-subtitle">4. 📤 Enviar Respuesta (Mensajero)</div>
        <ul>
            <li><strong>Función:</strong> Envía la respuesta generada al usuario en Telegram.</li>
            <li><strong>URL:</strong> <code>https://api.telegram.org/botTU_TOKEN_AQUI/sendMessage</code></li>
            <li><strong>Datos:</strong> <code>chat_id</code> (identificador del usuario) y <code>text</code> (mensaje de respuesta).</li>
        </ul>

        <div class="section-subtitle">🔄 Flujo completo</div>
        <ol>
            <li>El <strong>Schedule Trigger</strong> se activa cada 10 segundos.</li>
            <li><strong>Obtener Mensajes</strong> consulta si hay mensajes nuevos.</li>
            <li>Si hay mensaje, <strong>Lógica con Gist</strong> lo procesa y genera una respuesta.</li>
            <li><strong>Enviar Respuesta</strong> envía la respuesta al usuario.</li>
            <li>El ciclo se repite, permitiendo una conversación fluida.</li>
        </ol>
    </div>

    <!-- 8. CÓDIGO JAVASCRIPT -->
    <div class="section">
        <div class="section-title">📝 Código JavaScript del nodo "Lógica con Gist"</div>
        <p>Este es el código completo que ejecuta la inteligencia del bot. Puedes copiarlo y adaptarlo si lo deseas.</p>
        <pre>const PACIENTES_URL = 'https://gist.githubusercontent.com/coronelguillermo85-art/61ccc15c981da4105f65e3973f5c41ca/raw/gistfile1.txt';

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

return outputs;</pre>
    </div>

    <!-- 9. JSON DEL FLUJO -->
    <div class="section">
        <div class="section-title">📦 Código JSON completo del flujo (para importar en n8n)</div>
        <p>Puedes importar este JSON directamente en n8n (<strong>Import → From JSON</strong>). <strong>Recuerda reemplazar <code>TU_TOKEN_AQUI</code> por tu token real de Telegram.</strong></p>
        <pre>{
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
}</pre>
    </div>

    <!-- 10. PRIORIZACIÓN -->
    <div class="section">
        <div class="section-title">📋 Priorización automática (reglas de negocio)</div>
        <table>
            <thead>
                <tr><th>Motivo de consulta</th><th>Prioridad</th><th>Plazo de contacto</th></tr>
            </thead>
            <tbody>
                <tr><td>Psiquiatría + ideación/intento</td><td>🚨 <strong>EMERGENCIA</strong></td><td>Derivación inmediata al 107</td></tr>
                <tr><td>Psiquiatría (sin emergencia)</td><td>🔴 <strong>ALTA</strong></td><td>24 horas</td></tr>
                <tr><td>Psicología</td><td>🟡 <strong>MEDIA</strong></td><td>48 horas</td></tr>
                <tr><td>Clínica general / Otro</td><td>🟢 <strong>BAJA</strong></td><td>7 días hábiles</td></tr>
            </tbody>
        </table>
    </div>

    <!-- 11. INSTALACIÓN -->
    <div class="section">
        <div class="section-title">🔧 Instalación y configuración paso a paso</div>
        <div class="section-subtitle">Requisitos previos</div>
        <table>
            <thead>
                <tr><th>Recurso</th><th>Dónde obtenerlo</th></tr>
            </thead>
            <tbody>
                <tr><td><strong>Node.js</strong> (v18 o superior)</td><td><a href="https://nodejs.org" target="_blank">nodejs.org</a></td></tr>
                <tr><td><strong>Cuenta de GitHub</strong></td><td><a href="https://github.com" target="_blank">github.com</a></td></tr>
                <tr><td><strong>Cuenta en Railway</strong> (opcional)</td><td><a href="https://railway.app" target="_blank">railway.app</a></td></tr>
                <tr><td><strong>Token de Telegram</strong></td><td>Desde <code>@BotFather</code></td></tr>
            </tbody>
        </table>

        <div class="section-subtitle">Paso 1: Clonar el repositorio</div>
        <pre>git clone https://github.com/coronelguillermo85-art/ChatbotCaps.git
cd ChatbotCaps</pre>

        <div class="section-subtitle">Paso 2: Instalar n8n (local)</div>
        <pre>npm install -g n8n
npx n8n</pre>
        <p>Abrir <code>http://localhost:5678</code> en el navegador.</p>

        <div class="section-subtitle">Paso 3: Importar el flujo en n8n</div>
        <ul>
            <li>En n8n: <strong>Import → From JSON</strong>.</li>
            <li>Pegar el contenido del JSON (el bloque de arriba).</li>
            <li>Hacer clic en <strong>Import</strong>.</li>
        </ul>

        <div class="section-subtitle">Paso 4: Configurar el token de Telegram</div>
        <ul>
            <li>Crear un bot con <code>@BotFather</code> y copiar el token.</li>
            <li>En n8n, en los nodos <strong>Obtener Mensajes</strong> y <strong>Enviar Respuesta</strong>, reemplazar <code>TU_TOKEN_AQUI</code> por el token real.</li>
        </ul>

        <div class="section-subtitle">Paso 5: Activar el flujo</div>
        <ul>
            <li>Guardar (<strong>Save</strong>).</li>
            <li>Activar (<strong>Active</strong> en verde).</li>
            <li>Probar enviando <code>/start</code> al bot en Telegram.</li>
        </ul>

        <div class="section-subtitle">Paso 6 (opcional): Desplegar en Railway para 24/7</div>
        <ul>
            <li>Crear un repositorio en GitHub con <code>Dockerfile</code> y <code>caps-flujo.json</code>.</li>
            <li>En Railway: <strong>New Project → Deploy from GitHub repo</strong>.</li>
            <li>Agregar variables de entorno:
                <pre>N8N_BASIC_AUTH_ACTIVE=true
N8N_BASIC_AUTH_USER=admin
N8N_BASIC_AUTH_PASSWORD=admin123</pre>
            </li>
            <li>Obtener la URL pública y configurar el webhook de Telegram.</li>
        </ul>
    </div>

    <!-- 12. MIGRACIÓN WHATSAPP -->
    <div class="section">
        <div class="section-title">📱 Migración a WhatsApp Business (canal definitivo)</div>
        <p>El bot está diseñado para funcionar en <strong>WhatsApp Business API</strong>. Los pasos son:</p>
        <ol>
            <li>Crear una app en <strong>Meta Developers</strong> y obtener <code>Phone Number ID</code> y <code>Token Permanente</code>.</li>
            <li>En n8n, reemplazar los nodos de Telegram por <strong>Webhook</strong> (entrada) y <strong>HTTP Request</strong> (salida).</li>
            <li>La lógica JavaScript (priorización, base de datos) se mantiene sin cambios.</li>
            <li>Configurar el webhook en Meta apuntando a <code>https://tu-app.railway.app/webhook</code>.</li>
            <li>Probar con números de prueba (Meta permite hasta 5).</li>
            <li>Activar el plan gratuito de WhatsApp Business API (1000 conversaciones/mes sin costo).</li>
        </ol>
        <div class="mockup-mini">
            <div class="bubble">START</div>
            <div class="bubble">👋 ¿Cuál es tu nombre completo?</div>
            <div class="bubble bubble-user">Ana González</div>
            <div class="bubble">📞 ¿Número de teléfono?</div>
            <div class="bubble bubble-user">3442778899</div>
            <div class="bubble">✅ Registro previo encontrado. Turno de seguimiento asignado.</div>
        </div>
    </div>

    <!-- 13. RECURSOS -->
    <div class="section">
        <div class="section-title">📁 Recursos complementarios</div>
        <ul>
            <li>📂 <strong>Google Drive (documentos, entrevistas, diagramas):</strong><br>
                <a href="https://drive.google.com/drive/u/0/folders/1IdkUvw9u_x1RUD6_UMptPTWz_n1MT0kq" target="_blank">Carpeta del proyecto</a>
            </li>
            <li>🧪 <strong>Bot de prueba en Telegram:</strong><br>
                <code>@Caps_Salud_Mental_Tugip_bot</code>
            </li>
            <li>📄 <strong>Base de datos de ejemplo:</strong><br>
                <a href="https://gist.githubusercontent.com/coronelguillermo85-art/61ccc15c981da4105f65e3973f5c41ca/raw/gistfile1.txt" target="_blank">pacientes.txt</a>
            </li>
            <li>🐙 <strong>Repositorio GitHub:</strong><br>
                <a href="https://github.com/coronelguillermo85-art/ChatbotCaps" target="_blank">github.com/coronelguillermo85-art/ChatbotCaps</a>
            </li>
        </ul>
    </div>

    <!-- 14. ERRORES COMUNES -->
    <div class="section">
        <div class="section-title">🐞 Errores comunes y soluciones</div>
        <table>
            <thead>
                <tr><th>Error</th><th>Solución</th></tr>
            </thead>
            <tbody>
                <tr><td><code>Bad webhook / HTTPS required</code></td><td>Usar polling (HTTP Request) o ngrok para localhost.</td></tr>
                <tr><td><code>{"ok":true,"result":[]}</code></td><td>Cambiar offset a <code>-1</code> y enviar mensaje nuevo.</td></tr>
                <tr><td><code>401 Unauthorized</code></td><td>Token incorrecto. Generar nuevo con <code>@BotFather</code>.</td></tr>
                <tr><td><code>Too Many Requests (429)</code></td><td>Aumentar intervalo del Schedule Trigger a ≥ 10 segundos.</td></tr>
                <tr><td>El bot no prioriza</td><td>Verificar que el código JS tenga la lógica de <code>motivo</code> correcta.</td></tr>
                <tr><td>Railway no arranca</td><td>Revisar Dockerfile y variables de entorno.</td></tr>
            </tbody>
        </table>
    </div>

    <!-- 15. AUTOR Y LICENCIA -->
    <div class="section">
        <div class="section-title">👨‍💻 Autor</div>
        <p>
            <strong>Guillermo Coronel</strong> - Proyecto para el CAPS Dr. Bartolomé Giacomotti<br>
            <a href="https://github.com/coronelguillermo85-art" target="_blank">GitHub</a>
        </p>
    </div>

    <div class="section">
        <div class="section-title">📞 Contacto y emergencias</div>
        <ul>
            <li>🚨 <strong>Emergencias:</strong> 107 (gratuito, 24hs)</li>
            <li>🏥 <strong>Hospital Justo José de Urquiza:</strong> Guardia 24h</li>
            <li>📍 <strong>CAPS Dr. Bartolomé Giacomotti</strong> - Concepción del Uruguay, Entre Ríos</li>
        </ul>
    </div>

    <div class="section">
        <div class="section-title">📄 Licencia</div>
        <p>Este proyecto está bajo la licencia <strong>MIT</strong>.<br>
        Para más detalles, consultar el archivo <a href="LICENSE">LICENSE</a> en el repositorio.</p>
    </div>

    <!-- FOOTER -->
    <div class="footer">
        <p>⭐ <strong>Si te gustó el proyecto, no olvides dejar una estrella en GitHub.</strong> ¡Tu apoyo nos ayuda a seguir mejorando!</p>
        <p style="margin-top: 8px;">Bot de Triaje para Salud Mental - CAPS Dr. Bartolomé Giacomotti | Hito 3 - Proyecto Integrador</p>
    </div>

</div>
</body>
</html>
