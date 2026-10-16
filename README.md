# Axis

A free Cursor connector for the Axis account you already use.

Axis keeps a week in one place: tasks, projects, notes, calendar, habits, goals, a journal, health, and finances. This plugin connects Cursor to that account over [MCP](https://cursor.com/docs/mcp). You sign in with OAuth. There is no API key to paste, and nothing in this repository can see your data.

## What you can ask Cursor to do

Once you are signed in, Cursor can work in the parts of Axis you allow:

- **Tasks and projects** — look up what is open, add work, and mark it done
- **Notes** — find and write notes in your library
- **Calendar** — read your schedule and keep events current
- **Habits** — see routines and log what you actually did
- **Goals** — check progress and update the goals you are tracking
- **Journal** — read and write journal entries
- **Health** — log and review the health records you keep in Axis
- **Finances** — read and update the money records you choose to share

Writes land in your real account and show up in Axis the same way as if you had made them yourself.

## How access works

Install the plugin and connect **axis**. Cursor opens Axis and you sign in to your own account.

On the consent screen you pick the scopes. Read and write are separate for each area, so a connector can look at your calendar without being allowed to change it. You can leave out anything you do not want an agent to touch.

A few limits are fixed, not optional:

- The password vault is never accessible. Vault entries are not a scope, and no token from this connector can read them.
- Tokens issued here work only at `https://axisproductivityapp.com/mcp`. They are not a login to the rest of Axis.
- You can revoke a connector any time in Axis under **Settings → Agent access**. Revoking it cuts off that token immediately.
- Your Axis data is not used for training.

The connector is free.

## Install

1. In Cursor, open **Customize** and install the Axis plugin, or add this repository as a marketplace.
2. Connect the **axis** server and approve the sign-in.
3. Choose the scopes you want on the Axis consent screen.

The server is a remote MCP endpoint:

```json
{
  "mcpServers": {
    "axis": {
      "type": "http",
      "url": "https://axisproductivityapp.com/mcp"
    }
  }
}
```

Authentication is OAuth. Axis supports dynamic client registration, so this package does not ship a client id, client secret, or any other credential.

## Privacy

This plugin is a manifest and a logo. It does not include application code, and it does not embed tokens. Axis holds the account data. Cursor receives only what the scopes you approved allow, and only while the connection stays authorized.

Disconnect or revoke access in **Settings → Agent access** whenever you want it to stop.
