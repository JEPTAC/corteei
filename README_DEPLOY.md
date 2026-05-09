# Electroingeniería · despliegue GitHub + Firebase

## Estructura

```text
public/                  app web PWA
firebase.json            configuración de Firebase Hosting
firestore.rules          reglas de Firestore
firestore.indexes.json   índices iniciales
package.json             scripts de despliegue
apps-script/Code.gs      receptor opcional para fotos en Google Drive
```

## Antes de publicar

1. Crear el proyecto en Firebase.
2. Activar Authentication con proveedor Email/Password.
3. Crear Firestore Database.
4. Copiar la configuración web del proyecto en `public/firebase-config.js`.
5. Reemplazar `REEMPLAZAR_PROJECT_ID` en `.firebaserc`.

## Comandos principales

```bash
npm install
npx firebase login
npx firebase use REEMPLAZAR_PROJECT_ID
npx firebase deploy
```

## GitHub

```bash
git init
git add .
git commit -m "Versión inicial trazabilidad logística"
git branch -M main
git remote add origin URL_DEL_REPOSITORIO
git push -u origin main
```

## Integración automática Firebase + GitHub

Desde la raíz del proyecto:

```bash
npx firebase init hosting:github
```

Seleccionar el repositorio y permitir que Firebase cree los workflows de GitHub Actions.

## Usuarios iniciales

Crear usuarios en Firebase Authentication y luego crear un documento en Firestore:

Colección: `users`

ID del documento: UID del usuario

Ejemplo:

```json
{
  "name": "Coordinador Logístico",
  "email": "logistica@empresa.com",
  "role": "logistica"
}
```

Roles disponibles:

```text
admin
ventas
logistica
alistamiento
facturacion
caja
despacho
inventarios
jefe_logistico
auditoria
gerencia
```

## Prueba local sin Firebase

La app conserva modo local si `public/firebase-config.js` no está configurado. Para prueba rápida:

```bash
cd public
python -m http.server 8080
```

Abrir:

```text
http://localhost:8080
```
