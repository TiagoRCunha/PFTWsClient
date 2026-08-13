# PFTWsClient — @pft/ws-client

SDK de cliente WebSocket para aplicações PFT.

## Visão geral

Pacote npm `@pft/ws-client` que encapsula a conexão WebSocket com o **PFTChat** (via Gateway): handshake autenticado, join/leave de canais, envio e recebimento de mensagens e reconexão com backoff.

## Stack

- TypeScript (framework-agnostic, consumido pelo PFTWeb)
- Dependência de contratos: `@pft/contracts` (versão exata)

## Requisitos

- Node 20+

## Uso

```ts
import { WsClient } from '@pft/ws-client';

const client = new WsClient({ url: 'wss://...', token });
await client.join('channel-id');
client.on('message', (msg) => console.log(msg));
```

## Publicação

- **SemVer estrito**; dependência por versão exata.
- Publicado no **GitHub Packages** (`@pft/ws-client`).

## Documentação

- Contexto no [Índice](https://github.com/TiagoRCunha/PFTDocs/blob/main/context/README.md).
- Decisão de criação: [Client Package](https://github.com/TiagoRCunha/PFTDocs/blob/main/adr/0015-ws-client-package.md).
