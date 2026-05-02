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

## 📂 Archivos del proyecto

| Archivo | Descripción |
|---------|-------------|
| `README.md` | Documentación del proyecto |
| `CAPS Bot - Con Gist (1).json` | Flujo exportado de n8n (sin credenciales) |
| `capturas/` | Imágenes del funcionamiento |

> ⚠️ **Nota de seguridad:** El archivo JSON exportado no contiene el token real de Telegram. Para usar el flujo, deberás agregar tu propio token en los nodos correspondientes.

## 🗄️ Base de datos

La base de datos de pacientes se aloja en un **archivo público de GitHub Gist** para que el bot pueda leerla en tiempo real.

**Base de ejemplo (datos ficticios):**
👉 [pacientes.txt - Base de datos del bot](https://gist.githubusercontent.com/coronelguillermo85-art/61ccc15c981da4105f65e3973f5c41ca/raw/gistfile1.txt)

**Formato de cada registro (CSV con separador `|`):**
```text
NOMBRE|TELÉFONO|EDAD|SEXO|MOTIVO|TIEMPO|TRATAMIENTO|PRIORIDAD
Ejemplo|3442123456|37|Masculino|Psiquiatría|más de 3 meses|No|ALTA
