# @ai-chat/contracts

Shared, framework-free TypeScript types for the AI Chat API. These mirror the request/response DTOs of `ai-chat-api` **without** any `@nestjs/swagger` / `class-validator` runtime dependencies, so the frontend can import them safely.

## Install (private git)

```jsonc
// frontend package.json
{
  "dependencies": {
    "@ai-chat/contracts": "git+ssh://git@github.com/<org>/ai-chat-contracts.git#v0.0.1"
  }
}
```

Pin to a tag (`#v0.0.1`) or commit SHA so upgrades are explicit. Bump the tag whenever the API contract changes.

## Usage

```ts
import type { ListConversationsResponse, OpenConversationRequest } from '@ai-chat/contracts';
import { Platform, ChatMode } from '@ai-chat/contracts';

const body: OpenConversationRequest = { platform: Platform.OPENAI, model: 'gpt-4o-mini', message: 'hi' };
```

## Keeping in sync

These types are hand-mirrored from `ai-chat-api`'s DTOs. When a DTO changes, update the matching type here and publish a new tag. The API's DTO classes should `implements` the corresponding interface from this package so the compiler catches drift.
