# Isho's Factory Web

Sitio público de Isho's Factory con menú, configurador interactivo de sorbetes, carrito, preórdenes, panel operativo, Rewards e integraciones de WhatsApp.

## Documentación

- [Arquitectura técnica](docs/ARQUITECTURA.md)

La documentación cubre:

- Arquitectura general y estructura del repositorio.
- Flujo completo del configurador de sorbetes.
- Modelo de datos de Firestore.
- Panel de preórdenes y ciclo de estados.
- Integraciones de CallMeBot y la API privada de tickets en AWS.
- Seguridad actual y arquitectura recomendada.
- Operación, despliegue y estrategia de pruebas.

También está disponible la versión estructurada en Word: [Arquitectura técnica en Word](docs/Arquitectura_Ishos_Factory.docx).

> Estado: el sitio y el flujo de tickets están en desarrollo y pruebas. La API privada de WhatsApp funciona en AWS mediante un túnel HTTPS temporal; antes de producción debe migrarse a un dominio estable.

## Vista previa local

```bash
python3 -m http.server 4173 --directory public
```

Después abre `http://localhost:4173/`.

## Despliegue

La API de tickets se ejecuta de forma persistente en AWS como una aplicación FastAPI y se publica mediante un túnel HTTPS. La web solicita `POST /ticket`; el backend valida teléfono y contenido, limita solicitudes por IP y serializa el acceso a la sesión de WhatsApp Web.
La web usa el endpoint `/ticket` de esa URL tanto en Firebase Hosting como durante el desarrollo local.

```bash
firebase deploy --only hosting
```

```bash
firebase deploy --only firestore:rules
```

Prueba las reglas de Firestore antes de publicarlas.
