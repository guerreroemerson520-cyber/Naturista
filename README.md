# ECUAPERU — Catálogo de suplementos naturistas

## 1. Configura Supabase

1. Crea un proyecto en https://supabase.com/dashboard
2. Ve a **SQL Editor**, pega el contenido de `supabase_setup.sql` y presiona **Run**.
3. Ve a **Storage**, crea un bucket llamado exactamente `fotos-productos` y márcalo como **Public bucket**.
4. Ve a **Project Settings > API** y copia:
   - **Project URL**
   - **anon public key**
5. Abre `index.html`, busca estas líneas (cerca del final del archivo) y reemplázalas con tus valores:
   ```js
   const SUPABASE_URL = "https://TU-PROYECTO.supabase.co";
   const SUPABASE_ANON_KEY = "TU_LLAVE_ANON_PUBLICA";
   ```

## 2. Publica el sitio en GitHub Pages

1. Crea un repositorio nuevo en GitHub (puede ser público).
2. Sube estos archivos a la raíz del repositorio:
   - `index.html`
   - `hero-1.png`, `hero-2.png`, `hero-3.png`
   - `logo-ecuaperu.png`
3. Ve a **Settings > Pages** en el repositorio, en "Source" elige la rama `main` y carpeta `/ (root)`, guarda.
4. En 1-2 minutos tu sitio estará en `https://tu-usuario.github.io/nombre-del-repo/`

## Notas importantes

- **Seguridad del panel admin**: la clave (`CLAVE_ADMIN`) sigue siendo solo una verificación en el navegador,
  igual que antes — no es una autenticación real. Cualquiera con conocimientos técnicos podría agregar o
  borrar productos sin la clave, inspeccionando el código. Para un negocio real a futuro, lo ideal es migrar
  a **Supabase Auth** (login real) y restringir las políticas de la base de datos a usuarios autenticados.
  Por ahora, mantuve el mismo nivel de seguridad que ya tenía tu app para no complicar el primer despliegue.
- **Fotos**: ahora se suben al bucket de Supabase Storage y se guarda el link público en la base de datos,
  en vez de guardarse como texto pesado en el navegador. Esto también soluciona el problema de "la foto es
  muy pesada" que tenía la versión anterior.
- Cualquier producto que agregues desde el panel admin ahora lo ve cualquier persona que visite el sitio,
  desde cualquier dispositivo, al instante.
