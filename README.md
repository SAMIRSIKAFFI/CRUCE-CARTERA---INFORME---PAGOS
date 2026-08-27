# 📊 Sistema de Cruce de Cobranzas — VIVA

Herramienta web para verificar qué pagos de la cartera de cobranzas tienen la gestión registrada correctamente, a fin de presentar el informe de comisiones a VIVA.

---

## ¿Qué hace esta aplicación?

1. **Carga las carteras asignadas** (uno o varios archivos Excel del 1° de mes).
2. **Carga la base de pagos** subida al sistema de cobranza.
3. **Carga el informe de gestiones** generado por el sistema de cobranza.
4. **Cruza los tres archivos** aplicando las reglas de validación:
   - ✅ El código de cobranza del pago debe existir en la cartera asignada.
   - ✅ El código debe aparecer en el informe de gestión.
   - ✅ La fecha de gestión debe ser **igual o anterior** a la fecha de pago (nunca posterior).
   - ✅ **Vigencia:** la gestión no puede ser más antigua que el **1° día del mes anterior** al pago (ej. pago el 20/08 → gestión válida desde el 01/07 en adelante; una gestión de junio o antes no cuenta, aunque sea anterior al pago).
5. **Genera un Excel de observados** con todos los códigos que no cumplen las condiciones, listo para presentar a VIVA.

---

## Formatos de archivo requeridos

### Cartera asignada (Paso 1)
```
PERIODO_FACTURA | ID_CLIENTE | ID_COBRANZA | REPRESENTANTE_LEGAL | NOMBRE_CLIENTE | ...
```

### Base de pagos (Paso 2)
```
Periodo | Producto | Id Cobranza | Ciudad | Importe | Fecha pago
```

### Informe de gestión (Paso 3)
```
PRODUCTO | ID CLIENTE | NOMBRE CLIENTE | FECHA | ETAPA | SUBETAPA | ACTIVIDAD | PRÓXIMO PASO | ...
```

---

## Uso rápido

1. Abre `index.html` directamente en tu navegador (doble clic) **o** accede vía GitHub Pages (ver abajo).
2. Sigue los 5 pasos del panel lateral.
3. Descarga el Excel de observados al finalizar.

> No requiere instalación ni conexión a internet (salvo para GitHub Pages).

---

## Cómo publicar en GitHub Pages (paso a paso)

### Opción A — Subir archivos desde el navegador (más fácil)

1. Ve a [https://github.com](https://github.com) e inicia sesión.
2. Haz clic en el botón verde **"New"** (o el ícono **+** → "New repository").
3. Completa:
   - **Repository name:** `viva-cobranza` (o el nombre que prefieras)
   - **Description:** "Sistema de cruce de carteras VIVA"
   - Marca **Public** (necesario para GitHub Pages gratuito)
   - Marca ✅ **"Add a README file"**
4. Haz clic en **"Create repository"**.
5. Dentro del repositorio recién creado, haz clic en **"Add file" → "Upload files"**.
6. Arrastra el archivo `index.html` y el `README.md` al área de carga.
7. En la sección **"Commit changes"** escribe un mensaje como `Primera versión`.
8. Haz clic en **"Commit changes"** (botón verde).

### Activar GitHub Pages

1. En tu repositorio, haz clic en **"Settings"** (engranaje, arriba a la derecha).
2. En el menú izquierdo, haz clic en **"Pages"**.
3. En **"Source"**, selecciona:
   - Branch: `main`
   - Folder: `/ (root)`
4. Haz clic en **"Save"**.
5. Espera ~1 minuto y recarga la página.
6. Verás el enlace: `https://TU_USUARIO.github.io/viva-cobranza/`

¡Listo! Puedes compartir ese enlace con tu equipo.

---

### Opción B — Usar Git desde la terminal (para usuarios avanzados)

```bash
# 1. Clona el repositorio vacío que creaste en GitHub
git clone https://github.com/TU_USUARIO/viva-cobranza.git

# 2. Entra al directorio
cd viva-cobranza

# 3. Copia el archivo index.html aquí
# (pega index.html en esta carpeta)

# 4. Agrega, confirma y sube
git add .
git commit -m "Primera versión del sistema de cruce"
git push origin main
```

---

## Notas técnicas

- La aplicación funciona **100% en el navegador** (HTML + JavaScript puro).
- Utiliza la librería [SheetJS](https://sheetjs.com/) para leer y escribir archivos Excel.
- **No envía ningún dato a internet** — todo el procesamiento ocurre localmente.
- Compatible con Chrome, Edge y Firefox modernos.

---

## Estructura del proyecto

```
viva-cobranza/
├── index.html   ← Toda la aplicación (un solo archivo)
└── README.md    ← Este archivo
```

---

## Actualizar la aplicación

Si necesitas actualizar la app:
1. Modifica `index.html` localmente.
2. En GitHub, entra al archivo → haz clic en el ícono ✏️ (lápiz) → pega el nuevo contenido → "Commit changes".

---

## Licencia

Uso interno — Estudio Jurídico / Cobranzas VIVA.
