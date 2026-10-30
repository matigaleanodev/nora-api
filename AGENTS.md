# nora-api

## Contexto de trabajo

Si existe un workspace con AGENTS.md en los directorios padre, leerlo explícitamente antes de editar y seguir sus referencias. Una raíz Git anidada puede impedir la herencia automática. Fuera de ese entorno, este archivo y el README deben ser suficientes para trabajar.

## Estructura y límites

- Scaffold AWS CDK TypeScript para backend opcional de Nora.
- Entrada bin/nora-api.ts; stack lib/nora-api-stack.ts; pruebas en test/.
- La app offline no depende de este repositorio.
- No inferir existencia de rutas, autenticación, base de datos o sincronización desde el scaffold.
- Elegir persistencia y autenticación desde contratos y patrones de acceso explícitos.
- Restauración de backup y sincronización entre dispositivos son responsabilidades distintas.

## Desarrollo y verificación

- npm ci instala; npm run build compila; npm test ejecuta Jest.
- npm run cdk -- synth produce CloudFormation; no demuestra una API ejecutable.
- Evitar lookups AWS en comprobaciones locales.
- Un laboratorio SAM/DynamoDB independiente no acredita integración de esta aplicación.
- Revisar README y cdk.json antes de cambiar comandos o entrypoints.

## Restricciones

- No agregar NestJS, microservicios por entidad ni almacenamiento duplicado sin necesidad concreta.
- Definir ownership en servidor y no confiar en owner IDs enviados por clientes.
- Definir versiones, tombstones, idempotencia y conflictos antes de implementar sincronización.
- Usar credenciales ficticias y endpoints explícitos en entornos locales.
- No ejecutar bootstrap, deploy ni sincronización como parte de build/tests.
