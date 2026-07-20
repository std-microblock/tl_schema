# TL Schema History

Versioned Telegram API schemas extracted from the official [TDLib](https://github.com/tdlib/td) Git history.

The sync script walks every commit that changed `td/generate/scheme/telegram_api.tl`, reads `MTPROTO_LAYER` from `td/telegram/Version.h` at the same commit, and retains the newest schema revision for each layer. This also captures schema fixes committed after a layer was introduced.

TDLib's `MTPROTO_LAYER` history starts at layer 98. Each `schemas/layer-N.tl` file is stored as readable TL, and `schemas/manifest.json` records its source commit, SHA-256 digest, and byte size.

## Sync

```sh
npm run sync -- --td-repo ../td
npm test
```

The daily GitHub Actions workflow checks out TDLib with full history, runs the tests and sync, then commits only when generated files changed.
