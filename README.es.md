# Nora API

[English](README.md)

Scaffold AWS CDK TypeScript para el backend cloud opcional de Nora. La app Android funciona offline sin depender de este repositorio.

## Estructura

- bin/nora-api.ts: entrada de la aplicación CDK.
- lib/nora-api-stack.ts: stack de aplicación.
- test/: pruebas de infraestructura.
- cdk.json: configuración de ejecución CDK.

El stack está vacío: no expone rutas HTTP, autenticación, almacenamiento ni sincronización. La infraestructura usa AWS CDK v2; las herramientas de desarrollo usan TypeScript y Jest, con versiones resueltas en package-lock.json.

## Desarrollo local

```sh
npm ci
npm run build
npm test -- --runInBand
npm run cdk -- synth --no-lookups
```

Build compila TypeScript y synth genera CloudFormation en cdk.out. Jest contiene un placeholder para el primer contrato de comportamiento; este scaffold vacío no tiene pruebas funcionales. Estos comandos no despliegan infraestructura. Los checks locales deben evitar context lookups de AWS y usar configuración ficticia explícita cuando corresponda.

## Restricciones

La app offline conserva independencia de servicios remotos. Restauración de backup y sincronización entre dispositivos son contratos distintos. La autorización del backend debe exigir ownership en servidor. Consultar AGENTS.md para las instrucciones técnicas del repositorio.

[Nora App](https://github.com/matigaleanodev/nora-app) · [AWS CDK](https://docs.aws.amazon.com/cdk/v2/guide/home.html)
