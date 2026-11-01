# Shadow Intelligence + Objetivos personalizados

## Qué incorpora
- Crear, editar y eliminar objetivos personales.
- Categoría, prioridad (alta/media/baja), fecha objetivo y descripción del resultado.
- Conserva los objetivos antiguos convirtiéndolos en objetivos generales.
- Envía a la IA objetivos activos, prioridad, fecha, horario, niveles de habilidades y métricas agregadas.
- Genera 5 misiones diarias, 2 semanales o 1 mensual bajo demanda.
- Mantiene la clave de OpenAI exclusivamente en el servidor.

## Instalación
1. En la raíz del repositorio, añade `shadow-intelligence.js`.
2. Añade `api/generate-missions.js` (crea la carpeta `api` si hace falta).
3. En `index.html`, cambia el final:
   `<script src="app.js"></script></body>`
   por:
   `<script src="app.js"></script><script src="shadow-intelligence.js"></script></body>`
4. Despliega el repositorio en Vercel. GitHub Pages por sí solo no ejecuta la función backend.
5. En Vercel > Project > Settings > Environment Variables, crea `OPENAI_API_KEY` con tu clave privada. Opcional: `SHADOW_AI_MODEL` (por defecto `gpt-4.1-mini`).
6. Vuelve a desplegar. Frontend y endpoint deben estar en el mismo dominio.

## Seguridad y límites
- Nunca pongas `OPENAI_API_KEY` en `index.html`, JavaScript del navegador ni en GitHub.
- Configura límites de solicitudes y gasto en el proveedor/infraestructura. La protección principal debe estar en el perímetro (por ejemplo, Vercel Firewall/WAF); la función no incluye autenticación de usuarios y el control de frecuencia por instancia no es una defensa completa.
- No se envía el contenido del diario. Solo se envían categorías agregadas de actividad y métricas de rendimiento.
- Las misiones no alteran automáticamente atributos ni XP. El motor local conserva las recompensas.
- La generación es manual: pulsa el botón cuando quieras renovar el periodo.
