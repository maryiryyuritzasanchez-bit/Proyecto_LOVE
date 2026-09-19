# Fotos en la nube (para verlas en cualquier dispositivo)

Todo es gratis. Son 3 partes: crear la "bodega" de fotos, conectarla a la página y publicar la página.

## Parte 1 — Crear la bodega de fotos (Supabase)

1. Entra a https://supabase.com y crea una cuenta gratis.
2. Pulsa **New project**. Ponle un nombre (por ejemplo `modo-amor`), inventa una contraseña de base de datos (guárdala, aunque no la usaremos) y elige una región cercana (por ejemplo *South America (São Paulo)*). Espera un par de minutos a que termine de crearse.
3. En el menú izquierdo abre **SQL Editor** → **New query**.
4. Abre el archivo `supabase-setup.sql`, copia todo su contenido, pégalo ahí y pulsa **Run**. Debe decir "Success".

## Parte 2 — Conectar la bodega a la página

1. En Supabase abre **Project Settings** (el engranaje) → **API** (o el botón **Connect** arriba).
2. Copia dos datos:
   - **Project URL** (algo como `https://abcdefgh.supabase.co`)
   - La clave pública: **anon public** o **publishable** (es larga y empieza con `eyJ...` o `sb_publishable_...`). Nunca uses la clave `service_role` / `secret`.
3. Abre `index.html` con el Bloc de notas y busca `CONFIGURACIÓN DE LA NUBE`. Pega los datos entre las comillas:

```js
const SUPABASE_URL    = 'https://abcdefgh.supabase.co';
const SUPABASE_KEY    = 'eyJ...tu-clave...';
```

4. Guarda el archivo, ábrelo, entra y sube una foto. El texto sobre el botón debe decir "se guardan en la nube". Puedes comprobarlo en Supabase → **Storage** → carpeta `fotos`.

Las fotos que ya hubieras subido en ese dispositivo antes de conectar la nube se suben solas la primera vez.

## Parte 3 — Publicar la página para abrirla desde cualquier dispositivo

1. Entra a https://app.netlify.com/drop
2. Arrastra la carpeta completa del proyecto (con `index.html`, `siguiente.html`, `style.css` y la carpeta `stickers`).
3. Netlify te da un enlace `https://algo.netlify.app`. **Crea una cuenta gratis y "reclama" el sitio** para que no caduque.
4. Ese enlace es el que abren ustedes dos, desde el celular o el computador. Las fotos serán las mismas en todos.

Para actualizar la página más adelante, arrastra de nuevo la carpeta actualizada al mismo sitio (en la sección **Deploys**).

## Cosas que conviene saber

- **Pausa por inactividad:** el plan gratuito de Supabase pausa el proyecto si pasan 7 días sin uso. No se borra nada; si un día no cargan las fotos, entra a Supabase y pulsa **Restore project**. Abrir la página al menos una vez por semana lo evita.
- **Espacio:** el plan gratis da 1 GB. La página reduce cada foto antes de subirla, así que caben cientos.
- **Privacidad:** el candado de "usuario y contraseña" de la página solo es decorativo (está en el código). Quien tenga el enlace de la página podría abrirla, y quien conozca la dirección y la clave de Supabase podría ver, subir o borrar fotos. No compartan el enlace con nadie. Si en el futuro quieren un candado real, se puede agregar un inicio de sesión de verdad.
