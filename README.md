# Nora API

[Español](README.es.md)

AWS CDK TypeScript scaffold for the optional Nora cloud backend. The Android app works offline without this repository.

## Structure

- bin/nora-api.ts: CDK application entrypoint.
- lib/nora-api-stack.ts: application stack.
- test/: infrastructure tests.
- cdk.json: CDK execution configuration.

The stack is empty: it does not expose HTTP routes, authentication, storage or synchronization. Infrastructure uses AWS CDK v2; application tooling uses TypeScript and Jest, with resolved versions in package-lock.json.

## Local development

```sh
npm ci
npm run build
npm test -- --runInBand
npm run cdk -- synth --no-lookups
```

Build compiles TypeScript and synthesis generates CloudFormation in cdk.out. Jest contains a placeholder for the first behavior contract; there are no behavior tests for this empty scaffold. These commands do not deploy infrastructure. Local checks must avoid AWS context lookups and use explicit synthetic configuration when needed.

## Constraints

The offline app remains independent of remote services. Backup restoration and device synchronization are distinct contracts. Backend authorization must enforce ownership server-side. Consult AGENTS.md for repository-specific development instructions.

[Nora App](https://github.com/matigaleanodev/nora-app) · [AWS CDK](https://docs.aws.amazon.com/cdk/v2/guide/home.html)
