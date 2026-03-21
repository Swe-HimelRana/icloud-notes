## ADDED Requirements

### Requirement: Automatic Display Server Detection
The system SHALL automatically detect whether the Linux environment is running Wayland or X11 and configure the Electron Ozone platform accordingly.

#### Scenario: Launch in Wayland environment
- **WHEN** the application is launched in a session where `XDG_SESSION_TYPE` is `wayland`
- **THEN** the system SHALL initialize with `ozone-platform=wayland` (via `auto` detection)

#### Scenario: Launch in X11 environment
- **WHEN** the application is launched in a session where `XDG_SESSION_TYPE` is `x11`
- **THEN** the system SHALL initialize with `ozone-platform=x11` (via `auto` detection)

### Requirement: Wayland Protocol Access for Snap
The Snap package configuration SHALL include the `wayland` plug to allow the application to communicate with the Wayland compositor.

#### Scenario: Snap execution on Wayland
- **WHEN** the application is installed as a Snap and run on a Wayland-based distribution
- **THEN** the application SHALL be able to access the Wayland socket without permission errors

### Requirement: Support for HiDPI Scaling on Wayland
The system SHALL support native Wayland fractional scaling to ensure crisp text and UI elements on high-density displays.

#### Scenario: HiDPI display usage
- **WHEN** the application is running natively on Wayland with a HiDPI monitor
- **THEN** the UI SHALL be rendered at the native resolution of the display without XWayland-induced blurring
