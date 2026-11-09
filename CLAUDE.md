# Reglas del proyecto

- **Nunca subir cambios directo a `main`.** Todo cambio va en una rama (`fase-N` o `fix-...`) con pull request.
- `main` solo recibe lo que Kevin (dueño del repo) probó y aprobó en el enlace de prueba de Vercel.
- Cada pull request incluye: qué cambió y una lista de qué probar.
- Idioma de la interfaz, el código de dominio y los mensajes de commit: español.
- **La base de datos ya no se cambia desde este repositorio.** Desde el 9-nov-2026 el gestor comparte el proyecto de Supabase con `teggnar-plataforma`, que es el único dueño de las migraciones (también las de las tablas del gestor) y de la configuración de Auth (ADR-0010 en ese repositorio). Un cambio de esquema del gestor = pull request en `teggnar-plataforma`, con copia de seguridad antes. Nada de cambios manuales en el panel de Supabase.

# Contexto

App interna de gestión de proyectos y tareas del equipo (3 socios). Multi-espacio desde el inicio para poder ofrecerla a clientes después.
Stack: Next.js 15 (App Router) · Supabase (Auth Google, Postgres con RLS) · Tailwind · dnd-kit · Resend (correo) · WhatsApp Cloud API de Meta · Vercel. Recordatorios: `lib/notificar.ts` (envío) y `lib/recordatorios.ts` (reglas); `/api/cron/recordatorios` la llama Supabase pg_cron cada 15 min.
Esquema: las migraciones `0001`–`0008` de `supabase/migrations/` quedan como historial (congeladas); las vigentes viven en `teggnar-plataforma/supabase/migrations/`. Las tablas del gestor siguen en `public`; la plataforma usa el esquema `app`. Fases pendientes en el README.
