# FamiliaFit 🔥 — Guía de despliegue con GitHub + Vercel

## Archivos del proyecto

```
familiafit/
├── index.html    ← app principal
└── widget.html   ← widget de racha para home screen
```

---

## Paso 1 — Configurar Firebase

### 1.1 Crear el proyecto
1. Ve a **https://console.firebase.google.com**
2. **"Agregar proyecto"** → nombre: `familiafit` → desactiva Analytics → **Crear**

### 1.2 Crear la base de datos
1. Menú izquierdo → **Compilación → Realtime Database**
2. **"Crear una base de datos"** → región `us-central1` → **modo de prueba** → Habilitar

### 1.3 Obtener credenciales
1. ⚙️ Configuración del proyecto → pestaña **"General"**
2. Baja a **"Tus apps"** → clic en **`</>`** (Web) → nombre: `familiafit` → Registrar
3. Copia el objeto `firebaseConfig` completo

### 1.4 Pegar credenciales
Abre **tanto** `index.html` **como** `widget.html` y en cada uno reemplaza:

```javascript
const firebaseConfig = {
  apiKey: "REEMPLAZA_CON_TU_API_KEY",
  authDomain: "REEMPLAZA.firebaseapp.com",
  databaseURL: "https://REEMPLAZA-default-rtdb.firebaseio.com",
  ...
};
```

con tu bloque real. **Ambos archivos deben tener las mismas credenciales.**

---

## Paso 2 — Subir a GitHub

1. Ve a **https://github.com/new**
2. Nombre del repositorio: `familiafit`
3. Visibilidad: **Público** (necesario para Vercel gratis) o Privado si tienes plan
4. **"Create repository"**
5. En la página del repo recién creado, clic en **"uploading an existing file"**
6. Arrastra `index.html` y `widget.html` → **"Commit changes"**

---

## Paso 3 — Desplegar con Vercel

1. Ve a **https://vercel.com** → **"Sign Up"** con tu cuenta de GitHub
2. Clic en **"Add New Project"**
3. Selecciona el repositorio `familiafit`
4. Vercel lo detecta automáticamente como proyecto estático
5. Clic en **"Deploy"** — listo en ~30 segundos

Tu app queda en una URL tipo:
```
https://familiafit-tuusuario.vercel.app
```

Puedes cambiarla en **Settings → Domains** dentro del proyecto en Vercel.

---

## Paso 4 — Compartir con la familia

### App principal
```
https://familiafit-tuusuario.vercel.app/index.html
```

### Widget de racha (uno por persona)
```
NY     → https://familiafit-tuusuario.vercel.app/widget.html?m=ny
Moni   → https://familiafit-tuusuario.vercel.app/widget.html?m=moni
Nico   → https://familiafit-tuusuario.vercel.app/widget.html?m=nico
Tincho → https://familiafit-tuusuario.vercel.app/widget.html?m=tincho
```

Cada uno abre **su** link del widget y lo agrega al home screen:
- **iPhone** → Safari → botón compartir (□↑) → "Agregar a pantalla de inicio"
- **Android** → Chrome → menú (⋮) → "Añadir a pantalla de inicio"

---

## Paso 5 — Futuras actualizaciones

Cuando quieras cambiar algo en el código:
1. Edita el archivo en GitHub directamente (clic en el archivo → ✏️ editar)
2. Haz **"Commit changes"**
3. Vercel detecta el cambio y redespliega automáticamente en ~20 segundos

---

## Reglas de seguridad Firebase (después de 30 días)

El modo de prueba expira. Antes de que pase, ve a:
**Firebase Console → Realtime Database → Reglas** y pega:

```json
{
  "rules": {
    "familiafit": {
      ".read": true,
      ".write": true
    }
  }
}
```

Publica los cambios. Esto mantiene acceso libre (suficiente para uso familiar).

---

## Resumen de la familia

| ID | Nombre | Emoji | Color widget |
|----|--------|-------|--------------|
| `ny` | NY | 🧔 | Naranja |
| `moni` | Moni | 👩 | Azul |
| `nico` | Nico | 🧑‍💻 | Verde |
| `tincho` | Tincho | 🧑 | Violeta |

Para cambiar emojis, nombres o roles, edita el array `MEMBERS` en ambos archivos.

---

## Reglas del reto

- 🗓 Empieza el **miércoles 20 de mayo de 2025**
- 💸 **$5.000 COP** por cada día sin registrar
- ✏️ Se puede editar hasta **7 días atrás** desde la pantalla principal
- 🏆 El pozo se decide entre todos a fin de mes
