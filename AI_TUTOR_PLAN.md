# Lilly's English Studio — AI Tutor V1

## Estado
Rama de desarrollo aislada de main. La web publicada no se modifica.

## Objetivo
Conversación libre en inglés B1–C2 con seguimiento de contexto, preguntas de profundización, corrección respetuosa y memoria de errores.

## Flujo
1. Elegir nivel, tema y modo (debate, entrevista, conversación, role play).
2. Enviar mensaje escrito o transcripción de voz.
3. Backend autenticado llama al modelo de IA, nunca directamente desde GitHub Pages con una clave secreta.
4. Mostrar respuesta contextual y opción de reproducir voz.
5. Al terminar, generar informe: naturalidad, gramática, vocabulario, fluidez y tres ejercicios personalizados.
6. Guardar historial privado por usuario en Supabase.

## Prompt de la profesora
You are Lilly's English tutor for an adult university-trained English and translation graduate returning to active practice. Converse naturally in English at the selected CEFR level. Ask one thoughtful follow-up at a time, referring specifically to the learner's previous message. Do not follow a fixed script or praise every answer. Be intellectually challenging, kind and encouraging. During conversation, prioritize flow; only interrupt for errors that block understanding. When the learner requests feedback or ends a session, give precise corrections with original phrase, improved phrase, explanation, and a new practice prompt. Do not claim to assess pronunciation from plain text. Respect learner-selected topics and boundaries.

## Seguridad y privacidad
- Supabase Auth y políticas RLS por auth.uid().
- Tablas nuevas con prefijo les_; no reutilizar tablas de SBM.
- Secretos de proveedores de IA solo en Edge Function Secrets.
- No registrar textos personales en logs públicos.
- Limitar solicitudes y gasto; definir política de retención y eliminación de conversaciones.
- La app debe indicar claramente cuando la IA no está disponible.

## Próximo bloque de implementación
- Definir tablas les_sessions, les_messages, les_learning_notes y sus RLS.
- Crear Edge Function les-chat con validación JWT, rate limiting y proveedor IA configurable.
- Conectar el panel Role Play actual con endpoint real, sin romper las otras pestañas.
- Probar en rama y publicar únicamente tras verificar conversación, seguridad y costo.
