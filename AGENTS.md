# AGENTS.md — PFTWsClient

> Contexto para agentes de IA trabalhando neste repositório (SDK de cliente WebSocket).

## Bounded context

Cliente WebSocket reutilizável (`@pft/ws-client`): conexão autenticada, join/leave de canal, mensagens e reconexão. **Não** é o servidor WS (isso é o PFTChat) e **não** é o pacote de contratos (PFTContracts).

## Stack

- TypeScript puro (sem framework) — consumido pelo PFTWeb.
- Contratos via `@pft/contracts` (versão exata).

## Decisões que afetam este pacote (ADRs)

- ADR 0002: um repositório por microserviço — release independente.
- ADR 0010: o PFTChat termina a conexão WS; o Gateway faz o túnel WSS validando JWT — o cliente conversa com o Gateway e recebe claims verificados.
- ADR 0015: este pacote nasce em repositório próprio (fora do PFTWeb e do PFTContracts).

## Estrutura prevista

```
src/
  client.ts          # WsClient: connect, join, leave, on/off
  transport.ts       # camada socket (reconexão, heartbeat)
  messages.ts        # tipagem de mensagens via @pft/contracts
test/
```

## Regras

- SemVer estrito; publicação no GitHub Packages.
- Sem lógica de negócio de chat — apenas transporte e estado de conexão.
- Mensagens tipadas pelos contratos (`@pft/contracts`).

## Comandos

```bash
npm run lint
npm run test
npm run build
```

## Referências

- Decisão de criação: `PFTDocs/adr/0015-ws-client-package.md`.
- Índice de contexto: `PFTDocs/context/README.md`.
