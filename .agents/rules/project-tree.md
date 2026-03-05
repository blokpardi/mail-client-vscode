---
trigger: model_decision
description: structure lookup
---

# Project Tree

```
mail-client-vscode/
├── package.json              # Extension manifest, commands, menus, views
├── tsconfig.json             # TS config (ES2022, commonjs)
├── esbuild.js                # Bundler (HTML/CSS as text loaders)
├── .vscodeignore
├── docs/                     # Documentation assets (logo, screenshot)
├── .vscode/
│   ├── launch.json           # Extension Development Host launch
│   └── tasks.json            # Watch build task
├── resources/icons/
│   └── mail.svg              # Activity bar icon
├── dist/                     # Build output (esbuild → extension.js)
└── src/
    ├── extension.ts          # Entry point: activate/deactivate
    ├── types/
    │   ├── account.ts        # IMailAccount
    │   ├── folder.ts         # IMailFolder
    │   └── message.ts        # IMailMessage, IMailMessageDetail, IMailAddress, IMailAttachment
    ├── services/
    │   ├── accountManager.ts # CRUD accounts, SecretStorage passwords, EventEmitter
    │   ├── imapService.ts    # ImapFlow wrapper: connect, listFolders, getMessages, getMessage
    │   └── smtpService.ts    # Nodemailer wrapper: sendMail, testConnection
    ├── providers/
    │   └── mailExplorerProvider.ts  # TreeDataProvider<MailTreeItem>, auto-connect, folder cache
    ├── panels/
    │   ├── accountSettingsPanel.ts  # Webview: account config form (test connection, save)
    │   ├── messageListPanel.ts     # Webview: message table (date, from, subject, actions)
    │   ├── messageDetailPanel.ts   # Webview: message detail + reply/forward/delete
    │   ├── composePanel.ts         # Webview: compose form logic + state injection
    │   └── views/                  # Static templates for webviews (loaded via esbuild text-loader)
    │       ├── compose/
    │       │   ├── compose.html
    │       │   ├── compose.css
    │       │   └── compose.js
    │       └── messageDetail/
    │           ├── messageDetail.html
    │           ├── messageDetail.css
    │           └── messageDetail.js
    └── commands/
        ├── accountCommands.ts      # addAccount, editAccount, removeAccount, refreshAccount
        └── messageCommands.ts      # openFolder, openMessage, reply, replyAll, forward
```
