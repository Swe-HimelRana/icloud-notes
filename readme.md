# Unofficial iCloud Notes Desktop App for Linux

**Description:**

Access your iCloud Notes seamlessly with this unofficial desktop application. Enjoy a dedicated space for your notes, streamlining your experience and providing quick access directly from your desktop.

**Key Features:**

- **Sync with iCloud:** Effortlessly synchronize your notes across your devices using your iCloud account. Your important notes are available wherever you go.

- **Desktop Convenience:** Embrace the simplicity of a dedicated desktop app. Easily manage and organize your iCloud Notes for a more focused note-taking experience.

- **Notifications:** Stay organized with optional notifications for important notes and updates. Receive timely reminders to keep you on top of your tasks.

**How to Use:**

1. **Download:** Get started by downloading and installing the app on your desktop.

2. **Login:** Sign in with your iCloud credentials to securely access and manage your notes.

3. **Explore:** Browse, create, and edit your iCloud Notes seamlessly from your desktop.

4. **Receive Updates:** Stay informed with customizable notifications for essential notes.

**Please Note:**
This application is an independent project and is not affiliated with or endorsed by Apple Inc. It is designed to enhance the desktop experience for iCloud Notes users.

Simplify your note-taking routine and enjoy a dedicated desktop space for your iCloud Notes. Download the app now and bring your notes to the forefront!


# Changelog
## [1.2.0] - 2024-4-30
- Big update
- Updated Rendering Engine from Chrome version: 121 to 124
- In app notification added
- Added new fetures in (context menu)
    - now you can cut, undo, redo, reload, zoom in-out, reset zoom, toggle fullscreen
- Now this package also availble for native debian package
    - you can install using apt command
    - check https://mirror.himelrana.com
    - If you install from apt mirror your app loading will be more faster

## [1.1.0] - 2024-02-25
- Added a new feature (context menu)
    - Now you can copy, past, select, copy link
## [1.0.0] - 2024-01-19
- Initial release

## Installation

## using snap
```bash
    sudo snap install icloud-notes
```
## using native debian apt command

```bash
    # Add mirror.himelrana.com in your system
    sudo apt install curl
    sudo curl -fsSLo /usr/share/keyrings/himel.gpg https://66355b217734305f6607e3f6--mirror-himelrana.netlify.app/himel.gpg
    echo "deb [signed-by=/usr/share/keyrings/himel.gpg] https://66355b217734305f6607e3f6--mirror-himelrana.netlify.app/ stable main"|sudo tee /etc/apt/sources.list.d/himel-release list
    sudo apt update
```

```bash
    sudo apt install icloud-notes
```

Visit [Snapcraft Store](https://snapcraft.io/icloud-notes) and click **Install**.

Visit [Apt Mirror](https://mirror.himelrana.com)  and install using debian native **apt** command

## Build

### Development

```bash
node version: v20.12.2
electron version: ^30.0.1

```

```bash
npm install
npm start
```

### Production

```bash
npm install
npm run dist
```

## License

MIT
