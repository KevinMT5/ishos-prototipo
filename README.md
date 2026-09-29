# Isho's Factory Web

Sitio público de Isho's Factory con menú, configurador interactivo de sorbetes, carrito, preórdenes, panel operativo, Rewards e integraciones de WhatsApp.

## Documentación

- [Arquitectura técnica](docs/ARQUITECTURA.md)

La documentación cubre:

- Arquitectura general y estructura del repositorio.
- Flujo completo del configurador de sorbetes.
- Modelo de datos de Firestore.
- Panel de preórdenes y ciclo de estados.
- Integraciones de CallMeBot y TextMeBot.
- Seguridad actual y arquitectura recomendada.
- Operación, despliegue y estrategia de pruebas.

## Vista previa local

```bash
python3 -m http.server 4173 --directory public
```

Después abre `http://localhost:4173/`.

## Despliegue

```bash
firebase deploy --only hosting
firebase deploy --only firestore:rules
```

Prueba las reglas de Firestore antes de publicarlas.
