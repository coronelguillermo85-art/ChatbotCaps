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

### Flujo en n8n
![Flujo en n8n](https://github.com/user-attachments/assets/f69a3cf1-1703-44e1-acac-e334c6bd4c03)

### Conversación en Telegram
![Conversación en Telegram](https://github.com/user-attachments/assets/3499c84a-f9a6-4b6e-87c3-4615a657c2a3)

---

## 🔧 Instalación y configuración (paso a paso)

### Requisitos previos
| Requisito | Dónde obtenerlo |
|-----------|-----------------|
| **Node.js** (versión 18 o superior) | [https://nodejs.org](https://nodejs.org) |
| **n8n** | Se instala automáticamente |
| **Cuenta de Telegram** | [https://telegram.org](https://telegram.org) |
| **GitHub Gist** (para la base de datos) | [https://gist.github.com](https://gist.github.com) |

---

### Paso 1: Instalar n8n

**Windows (PowerShell como administrador):**
```powershell
npm install -g n8n
