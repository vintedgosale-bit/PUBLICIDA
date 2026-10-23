# Generador de anuncios para Vinted

Una sola página web (`index.html`) que crea títulos, descripción, hashtags, palabras clave, precios y mensajes para compradores. Es gratis, no tiene límites y no necesita a Claude ni una cuenta de pago.

## Motores (los eliges dentro de la página)

| Motor | Coste / límites | Fotos | Requisitos |
|---|---|---|---|
| **IA en tu navegador** ([WebLLM](https://github.com/mlc-ai/web-llm), código abierto) | Gratis e ilimitado; privado; sin internet después de la primera descarga | Sí, con el modelo «Phi-3.5 Vision» | Navegador con WebGPU: Chrome/Edge recientes (PC y Android), Safari 26+ |
| **Ollama** ([ollama/ollama](https://github.com/ollama/ollama), código abierto) | Gratis e ilimitado | Sí, con `gemma3` o `qwen2.5vl` | Ollama instalado en tu ordenador |
| **Servidor compatible con OpenAI** | Depende del servicio (Groq, OpenRouter, LM Studio, llama.cpp…) | Depende del modelo | URL + modelo (+ clave) |
| **Sin IA (plantillas)** | Gratis, ilimitado e instantáneo | No | Ninguno: funciona siempre, incluso sin conexión |

Si un motor de IA falla, la página genera el anuncio con plantillas para que no te quedes sin resultado.

## Publicarlo gratis en GitHub Pages (5 minutos)

1. Entra en github.com → **New repository** → nombre `vinted-generator` → **Public** → *Create*.
2. **Add file → Upload files** → sube `index.html` (y este README) → *Commit changes*.
3. **Settings → Pages** → *Source*: **Deploy from a branch** → *Branch*: `main` / `(root)` → *Save*.
4. Al cabo de un minuto la tienes en `https://TU-USUARIO.github.io/vinted-generator/`.
5. En el móvil, ábrela y elige **Añadir a pantalla de inicio** para usarla como una app.

Así funciona la IA del navegador (WebGPU necesita una página `https`). También puedes abrir `index.html` directamente en el ordenador.

## Usar Ollama (opcional, la mejor calidad con fotos)

```bash
ollama pull gemma3:4b          # modelo que también entiende fotos
OLLAMA_ORIGINS=* ollama serve  # permite que la página se conecte
```
En Windows, crea la variable de entorno `OLLAMA_ORIGINS` con el valor `*` y reinicia Ollama. En la página, elige el motor «Ollama» (dirección `http://localhost:11434/v1`).

## Privacidad

Los ajustes, el historial y las claves se guardan solo en tu navegador (`localStorage`). Con WebLLM y Ollama, tus fotos no salen de tu dispositivo.
