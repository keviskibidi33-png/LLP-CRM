# LLP CRM Frontend

Microfrontend del módulo **LLP ASTM D4318-17e1** para Geofal.

- Dominio productivo: `https://llp.geofal.com.pe`
- Backend API: `https://api.geofal.com.pe` (rutas `/api/llp`)
- Integración shell: `crm-geofal` vía iframe modal (`LLPModule`)

## Objetivo

- Registrar/editar ensayos LLP.
- Guardar estado en BD (`EN PROCESO`/`COMPLETO`).
- Exportar Excel con plantilla oficial `Template_LLP.xlsx`.
- Cerrar modal del CRM al finalizar guardado.

## Rutas

- `/` -> `LLPForm` (ruta principal productiva)
- `/llp` -> `LLPForm` (compatibilidad)
- `/proctor` -> `ProctorForm` (solo soporte técnico)

## Stack

- Vite + React + TypeScript
- Tailwind CSS
- Axios
- React Hot Toast

## Variables de entorno

- `VITE_API_URL=https://api.geofal.com.pe`
- `VITE_CRM_LOGIN_URL=https://crm.geofal.com.pe/login`

## Desarrollo local

```bash
npm install
npm run dev
```

## Cambios recientes (Febrero 2026)

- Normalización inteligente en `onBlur` para encabezado:
  - `Muestra`: `555` -> `555-SU-26`
  - `N OT`: `555` -> `555-26`
- Fechas inteligentes en `onBlur` (mismo criterio que CBR/Proctor):
  - `fecha_ensayo`, `revisado_fecha`, `aprobado_fecha`
  - Ejemplos: `1202` -> `12/02/26`, `1/2` -> `01/02/26`
- Panel lateral tipo Proctor con:
  - barra de avance general
  - estado por secciones (`OK` / `Pend.`)
  - tabla de resumen de cálculos LLP

## Validación recomendada

- Abrir formulario LLP en el CRM shell.
- Escribir valores rápidos en `Muestra`, `N OT` y fechas, luego salir del campo para validar formato automático.
- Confirmar que el panel lateral actualiza avance y estados en vivo.

## Deploy en Coolify

1. Crear servicio desde este repositorio (`LLP-CRM`).
2. Build type: `Dockerfile`.
3. Variables:
   - `VITE_API_URL=https://api.geofal.com.pe`
   - `VITE_CRM_LOGIN_URL=https://crm.geofal.com.pe/login`
4. Exponer puerto `80`.
5. Dominio:
   - `llp.geofal.com.pe`
