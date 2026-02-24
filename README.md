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

## Deploy en Coolify

1. Crear servicio desde este repositorio (`LLP-CRM`).
2. Build type: `Dockerfile`.
3. Variables:
   - `VITE_API_URL=https://api.geofal.com.pe`
   - `VITE_CRM_LOGIN_URL=https://crm.geofal.com.pe/login`
4. Exponer puerto `80`.
5. Dominio:
   - `llp.geofal.com.pe`
