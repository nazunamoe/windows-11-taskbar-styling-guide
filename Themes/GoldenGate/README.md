# Golden Gate Menu Bar theme for Windows 11 Taskbar Styler

A macOS 27 Golden Gate–inspired **top menu bar** for Windows 11. It turns the
taskbar into a full-width, 32px translucent strip at the top of the screen: a
small Apple glyph at the far left, compact app icons, and a right-side status
cluster with a one-line clock.

This is the top menu bar variant, not a floating dock.

**Author**: [nazunamoe](https://github.com/nazunamoe)

> [!NOTE]
> This is an unofficial fan-made theme. macOS, the macOS Golden Gate name, and
> the Apple logo are trademarks of Apple Inc. This theme is not affiliated with
> or endorsed by Apple. The Apple glyph in `Assets/apple.png` comes from
> [Simple Icons](https://simpleicons.org/) (CC0 1.0) and is included only for
> personal customization.

## Requirements

Install these Windhawk mods first:

* [Taskbar on top for Windows 11](https://windhawk.net/mods/taskbar-on-top) —
  set **Taskbar location** to **Top**. This is what actually moves the taskbar
  to the top of the screen. If the Start menu opens in an odd position, enable
  **Adjust Start menu animation** in the same mod.
* [Taskbar height and icon size](https://windhawk.net/mods/taskbar-icon-size) —
  required for a true 32px menu-bar height. Recommended values: **Taskbar height
  32**, **Icon size 18**, **Taskbar button width 30**. The style can resize the
  XAML content, but only this mod resizes the taskbar window itself.

The theme forces the task list to the left, so Windows' taskbar alignment
setting is less important. **Left** alignment still gives the most predictable
result.

## Suggested setup

- Use a dark wallpaper, ideally the Golden Gate Sunset/Night wallpaper or any
  blue-hour city photo.
- Set taskbar alignment to **Left**.
- Keep taskbar labels off.
- Leave **Click-through taskbar** off; the menu bar is a solid full-width strip.

## Design notes

- **Full-width menu bar** — no floating dock, no rounded corners, and no gap
  around the bar. It's a single edge-to-edge strip at the top of the screen.
- **Golden Gate sunset rim** — the bottom edge carries a horizontal gradient
  from sunset gold through International Orange and dusk rose into bay blue.
- **Tinted Liquid Glass** — `WindhawkBlur` gives the bar the frosted, slightly
  warm transparency of macOS 27's refined Liquid Glass.
- **Compact app strip** — 18px app icons, no labels, no running dots, and a
  subtle 5px-radius hover highlight. The Apple glyph sits at the far left like
  the Apple menu slot.
- **One-line status area** — network, volume, battery, language, chevron, and a
  small clock live directly on the bar. The date is hidden so the clock remains
  a single menu-bar-height line.
- **Quiet defaults** — Search, Widgets, Task View, Copilot, the notification
  bell, and the Show Desktop line are hidden.

> [!NOTE]
> The clock stays on the bar. The theme hides only the notification bell's text
> content and collapses the date line; it doesn't collapse the whole
> notification center button, because that can take the clock with it on some
> Windows builds.

## Palette

| Role | Value |
| --- | --- |
| Sunset gold | `#FFD39A` |
| Coral | `#FF8A5C` |
| Dusk rose | `#E8B4A0` |
| Bay blue | `#6FC7D9` |
| Glass tint | `#2A1C22` |
| Accent | `#F2A65A` |
| Primary text | `#F8F1E8` |

## Customization

The following style constants are exposed. Change them under **Style constants**
in the mod settings.

| Constant | Default | Purpose |
| --- | --- | --- |
| `BarHeight` | `32` | Height of the full-width menu bar |
| `ItemWidth` | `30` | Width of a Start/app button |
| `ItemHeight` | `26` | Height of a Start/app button |
| `IconSize` | `18` | App icon size |
| `TrayIconSize` | `14` | Tray image icon size |
| `ClockSize` | `12` | Clock font size |
| `MenuBarBackground` | tinted blur | Bar fill |
| `MenuBarBorder` | sunset gradient | Bottom rim light |
| `StartLogo` | Apple glyph | Start button image |
| `HoverFill` | `#26FFE0B8` | Warm hover highlight |
| `PressedFill` | `#3DFFE0B8` | Warm pressed highlight |
| `TextPrimary` | `#FFF8F1E8` | Clock and tray glyphs |
| `TextSecondary` | `#B8DCC9BE` | Secondary text such as the language indicator |
| `Accent` | `#FFF2A65A` | Progress bars and attention accents |

Golden Gate's Liquid Glass slider maps to the `TintOpacity` value inside
`MenuBarBackground`: lower it for clearer glass, or raise it for the more
opaque, tinted look that Apple added for legibility.

If a particular DPI or icon set still clips the right edge of an app icon, raise
`ItemWidth` to `32` or lower `IconSize` to `16`. The default geometry uses a
30px button with zero panel padding and a centered 18px icon.

The Start glyph is a small Apple silhouette loaded by `StartLogo`. The default
value points at the fork's raw asset URL. If you're applying the theme before
the asset is published, or you're offline, replace it with a local path:

```yaml
StartLogo=<ImageBrush Stretch="Uniform" ImageSource="C:\path\to\Themes\GoldenGate\Assets\apple.png" />
```

## Optional: a pure menu bar

By default the bar keeps small app icons after the Apple glyph. For a stricter
macOS-style menu bar with only the Apple slot and the status area, add this
control style after importing the theme:

Target:

```
Taskbar.TaskListButton
```

Style:

```
Visibility=Collapsed
```

This hides the app buttons but keeps the Apple glyph and the system tray.
Alt+Tab and Win+Tab still work for switching apps.

## Known limitations

- The taskbar must be at the top. The theme styles the bar; it doesn't move it.
  Install **Taskbar on top for Windows 11** and set it to **Top**.
- The Start button uses the bundled Apple silhouette instead of the native
  Windows glyph. Change `StartLogo` if you prefer another image.
- The date is hidden to keep the clock on one line. Use the [Taskbar Clock
  Customization](https://windhawk.net/mods/taskbar-clock-customization) mod if
  you want a formatted date and time together.
- Like every Taskbar Styler theme, it applies to every monitor. Per-monitor
  styling isn't supported.
- A side taskbar isn't supported; the theme expects a horizontal bar.

## Textual mode installation

1. Open the Windows 11 Taskbar Styler mod in Windhawk.
2. Go to the **Settings** tab and select **Textual mode**.
3. Copy the YAML below into the text box.
4. Click **Save settings**.

<details>
<summary>Content to import (click to expand)</summary>

```yaml
styleConstants:
  - BarHeight=32
  - ItemWidth=30
  - ItemHeight=26
  - IconSize=18
  - TrayIconSize=14
  - ClockSize=12
  - MenuBarBackground=<WindhawkBlur BlurAmount="32" TintColor="#2A1C22" TintOpacity="0.55" TintSaturation="1.15" TintLuminosityOpacity="0.3" NoiseOpacity="0.02" />
  - MenuBarBorder=<LinearGradientBrush StartPoint="0,0" EndPoint="1,0"><GradientStop Color="#4DFFD39A" Offset="0.0"/><GradientStop Color="#B3FFD39A" Offset="0.18"/><GradientStop Color="#66FF8A5C" Offset="0.5"/><GradientStop Color="#33E8B4A0" Offset="0.78"/><GradientStop Color="#4D6FC7D9" Offset="1.0"/></LinearGradientBrush>
  - StartLogo=<ImageBrush Stretch="Uniform" ImageSource="https://raw.githubusercontent.com/nazunamoe/windows-11-taskbar-styling-guide/main/Themes/GoldenGate/Assets/apple.png" />
  - HoverFill=#26FFE0B8
  - PressedFill=#3DFFE0B8
  - TextPrimary=#FFF8F1E8
  - TextSecondary=#B8DCC9BE
  - Accent=#FFF2A65A
controlStyles:
  - target: Taskbar.TaskbarFrame
    styles:
      - Height=$BarHeight
      - MinHeight=$BarHeight
      - MaxHeight=$BarHeight
      - HorizontalAlignment=Stretch
      - VerticalAlignment=Top
      - Background=Transparent
      - Padding=0
  - target: Taskbar.TaskbarFrame > Grid#RootGrid
    styles:
      - Padding=8,0,8,0
      - Background:=$MenuBarBackground
      - BorderBrush:=$MenuBarBorder
      - BorderThickness=0,0,0,1
      - CornerRadius=0
  - target: Taskbar.TaskbarBackground#BackgroundControl
    styles:
      - Visibility=Collapsed
  - target: Taskbar.TaskbarFrame > Grid#RootGrid > Taskbar.TaskbarBackground > Grid
    styles:
      - Background=Transparent
      - BorderThickness=0
  - target: Taskbar.TaskbarFrame > Grid#RootGrid > Taskbar.TaskbarBackground > Grid > Rectangle#BackgroundFill
    styles:
      - Fill=Transparent
  - target: Rectangle#BackgroundStroke
    styles:
      - Fill=Transparent
  - target: Taskbar.TaskbarFrame > Grid#RootGrid > Microsoft.UI.Xaml.Controls.ItemsRepeater#TaskbarFrameRepeater
    styles:
      - Width=Auto
      - HorizontalAlignment=Left
      - VerticalAlignment=Center
  - target: Taskbar.TaskListButton, Taskbar.ExperienceToggleButton
    styles:
      - Margin=0
      - Padding=0
      - MinWidth=0
      - HorizontalContentAlignment=Center
      - VerticalContentAlignment=Center
  - target: Taskbar.TaskListButtonPanel
    styles:
      - Width=$ItemWidth
      - Height=$ItemHeight
      - MinWidth=0
      - MaxWidth=$ItemWidth
      - Margin=0
      - Padding=0
      - HorizontalAlignment=Center
      - VerticalAlignment=Center
  - target: Grid#IconPanel, Taskbar.TaskListLabeledButtonPanel
    styles:
      - Width=$ItemWidth
      - Height=$ItemHeight
      - MinWidth=0
      - MaxWidth=$ItemWidth
      - Margin=0
      - Padding=0
      - HorizontalAlignment=Center
      - VerticalAlignment=Center
  - target: Grid#IconPanel > Image#Icon, Taskbar.TaskListLabeledButtonPanel#IconPanel > Image#Icon
    styles:
      - Width=$IconSize
      - Height=$IconSize
      - Margin=0
      - HorizontalAlignment=Center
      - VerticalAlignment=Center
      - Stretch=Uniform
  - target: Grid#IconPanel > TextBlock#LabelControl, Taskbar.TaskListLabeledButtonPanel > TextBlock#LabelControl
    styles:
      - Visibility=Collapsed
  - target: Taskbar.TaskListButtonPanel@CommonStates > Grid > Border#BackgroundElement, Taskbar.TaskListButtonPanel@CommonStates > Border#BackgroundElement
    styles:
      - Background=Transparent
      - Background@InactiveNormal=Transparent
      - Background@ActiveNormal=Transparent
      - Background@InactivePointerOver:=$HoverFill
      - Background@ActivePointerOver:=$HoverFill
      - Background@InactivePressed:=$PressedFill
      - Background@ActivePressed:=$PressedFill
      - BorderThickness=0
      - CornerRadius=5
      - Margin=1
  - target: Grid#IconPanel@CommonStates > Border#BackgroundElement, Taskbar.TaskListLabeledButtonPanel@CommonStates > Border#BackgroundElement
    styles:
      - Background=Transparent
      - Background@InactiveNormal=Transparent
      - Background@ActiveNormal=Transparent
      - Background@InactivePointerOver:=$HoverFill
      - Background@ActivePointerOver:=$HoverFill
      - Background@InactivePressed:=$PressedFill
      - Background@ActivePressed:=$PressedFill
      - Background@MultiWindowNormal=Transparent
      - Background@MultiWindowPointerOver:=$HoverFill
      - Background@MultiWindowActive=Transparent
      - Background@MultiWindowPressed:=$PressedFill
      - BorderThickness=0
      - CornerRadius=5
      - Margin=1
  - target: Taskbar.ExperienceToggleButton#LaunchListButton[AutomationProperties.AutomationId=StartButton] > Taskbar.TaskListButtonPanel > Grid > Microsoft.UI.Xaml.Controls.AnimatedVisualPlayer#Icon, Taskbar.ExperienceToggleButton#LaunchListButton[AutomationProperties.AutomationId=StartButton] > Taskbar.TaskListButtonPanel > Microsoft.UI.Xaml.Controls.AnimatedVisualPlayer#Icon
    styles:
      - Visibility=Collapsed
  - target: Taskbar.ExperienceToggleButton#LaunchListButton[AutomationProperties.AutomationId=StartButton]
    styles:
      - RequestedTheme=2
  - target: Taskbar.ExperienceToggleButton#LaunchListButton[AutomationProperties.AutomationId=StartButton] > Taskbar.TaskListButtonPanel@CommonStates > Grid > Border#BackgroundElement, Taskbar.ExperienceToggleButton#LaunchListButton[AutomationProperties.AutomationId=StartButton] > Taskbar.TaskListButtonPanel@CommonStates > Border#BackgroundElement
    styles:
      - Background:=$StartLogo
      - Background@InactiveNormal:=$StartLogo
      - Background@ActiveNormal:=$StartLogo
      - Background@InactivePointerOver:=$StartLogo
      - Background@ActivePointerOver:=$StartLogo
      - Background@InactivePressed:=$StartLogo
      - Background@ActivePressed:=$StartLogo
      - BorderBrush@InactivePointerOver:=$HoverFill
      - BorderBrush@ActivePointerOver:=$HoverFill
      - BorderBrush@ActiveNormal:=$HoverFill
      - BorderThickness=0
      - BorderThickness@InactivePointerOver=1
      - BorderThickness@ActivePointerOver=1
      - BorderThickness@ActiveNormal=1
      - CornerRadius=5
      - Margin=1
  - target: Grid#IconPanel@RunningIndicatorStates > Rectangle#RunningIndicator, Taskbar.TaskListLabeledButtonPanel@RunningIndicatorStates > Rectangle#RunningIndicator
    styles:
      - Visibility=Collapsed
  - target: Border#MultiWindowElement
    styles:
      - Visibility=Collapsed
  - target: Rectangle#DeterminateProgressBarIndicator, Rectangle#IndeterminateProgressBarIndicator, Rectangle#IndeterminateProgressBarIndicator2
    styles:
      - Fill=$Accent
  - target: Rectangle#ProgressBarTrack
    styles:
      - Fill=#33FFFFFF
  - target: Taskbar.ExperienceToggleButton#LaunchListButton[AutomationProperties.AutomationId=TaskViewButton]
    styles:
      - Visibility=Collapsed
  - target: SearchUx.SearchUI.SearchButtonControl, Taskbar.SearchBoxButton
    styles:
      - Visibility=Collapsed
  - target: Taskbar.AugmentedEntryPointButton#AugmentedEntryPointButton
    styles:
      - Visibility=Collapsed
  - target: Taskbar.TaskListButton#TaskListButton[AutomationProperties.Name=Copilot]
    styles:
      - Visibility=Collapsed
  - target: SystemTray.CopilotIcon#CopilotIcon
    styles:
      - Visibility=Collapsed
  - target: SystemTray.SystemTrayFrame
    styles:
      - Height=$BarHeight
      - Width=Auto
      - HorizontalAlignment=Right
      - VerticalAlignment=Top
      - Background=Transparent
      - Padding=0
  - target: StackPanel#SystemTrayFrameGrid, Grid#SystemTrayFrameGrid
    styles:
      - Height=$BarHeight
      - Margin=0
      - Padding=4,0,8,0
      - Background=Transparent
      - BorderThickness=0
      - CornerRadius=0
      - VerticalAlignment=Center
  - target: SystemTray.ImageIconContent > Grid#ContainerGrid > Image
    styles:
      - Width=$TrayIconSize
      - Height=$TrayIconSize
  - target: SystemTray.TextIconContent > Grid#ContainerGrid > SystemTray.AdaptiveTextBlock#Base > TextBlock#InnerTextBlock
    styles:
      - FontSize=13
      - Foreground:=$TextPrimary
  - target: SystemTray.AdaptiveTextBlock#LanguageInnerTextBlock > TextBlock#InnerTextBlock
    styles:
      - FontSize=11
      - FontWeight=SemiBold
      - Foreground:=$TextSecondary
  - target: SystemTray.NotifyIconView#NotifyItemIcon
    styles:
      - MinWidth=26
  - target: SystemTray.ChevronIconView
    styles:
      - MinWidth=24
  - target: SystemTray.OmniButton > Grid@CommonStates > Border#BackgroundBorder, SystemTray.NotifyIconView > Grid#ContainerGrid@ > Border#BackgroundBorder, SystemTray.IconView > Grid#ContainerGrid@ > Border#BackgroundBorder, SystemTray.ChevronIconView > Grid#ContainerGrid@ > Border#BackgroundBorder
    styles:
      - Background=Transparent
      - Background@PointerOver:=$HoverFill
      - Background@Pressed:=$PressedFill
      - BorderThickness=0
      - CornerRadius=5
  - target: SystemTray.DateTimeIconContent > Grid#ContainerGrid
    styles:
      - Background=Transparent
      - BorderThickness=0
      - CornerRadius=0
      - Margin=4,0,0,0
      - Padding=4,0,6,0
      - VerticalAlignment=Center
  - target: TextBlock#TimeInnerTextBlock
    styles:
      - Foreground:=$TextPrimary
      - FontFamily=Segoe UI Variable Display
      - FontSize=$ClockSize
      - FontWeight=SemiBold
      - Margin=0
      - VerticalAlignment=Center
  - target: TextBlock#DateInnerTextBlock
    styles:
      - Visibility=Collapsed
  - target: SystemTray.Stack#ShowDesktopStack
    styles:
      - Visibility=Collapsed
  - target: Grid#ContainerGrid@ > Rectangle#ShowDesktopPipe
    styles:
      - Visibility=Collapsed
  - target: SystemTray.OmniButton#NotificationCenterButton > Grid > ContentPresenter > ItemsPresenter > StackPanel > ContentPresenter > SystemTray.IconView#SystemTrayIcon > Grid > Grid > SystemTray.TextIconContent
    styles:
      - Visibility=Collapsed
  - target: Border#OverflowFlyoutBackgroundBorder
    styles:
      - Background:=$MenuBarBackground
      - BorderBrush:=$MenuBarBorder
      - BorderThickness=1
      - CornerRadius=10
      - RequestedTheme=2
  - target: MenuFlyoutPresenter
    styles:
      - CornerRadius=10
      - RequestedTheme=2
  - target: MenuFlyoutPresenter > Border
    styles:
      - Background:=$MenuBarBackground
      - BorderBrush:=$MenuBarBorder
      - BorderThickness=1
      - CornerRadius=10
      - Padding=5
  - target: Windows.UI.Xaml.Controls.FlyoutPresenter
    styles:
      - Background:=$MenuBarBackground
      - BorderBrush:=$MenuBarBorder
      - BorderThickness=1
      - CornerRadius=12
      - Padding=2
      - RequestedTheme=2
  - target: ToolTip > ContentPresenter#LayoutRoot
    styles:
      - Background:=$MenuBarBackground
      - BorderBrush:=$MenuBarBorder
      - BorderThickness=1
      - CornerRadius=7
      - Padding=6,3,6,3
      - Foreground:=$TextPrimary
  - target: ToolTip > ContentPresenter#LayoutRoot > TextBlock
    styles:
      - Foreground:=$TextPrimary
  - target: Taskbar.TaskbarBackground#HoverFlyoutBackgroundControl > Grid > Rectangle#BackgroundFill
    styles:
      - Fill:=$MenuBarBackground
  - target: Border#HoverFlyoutBackground
    styles:
      - Background=Transparent
      - BorderBrush:=$MenuBarBorder
      - BorderThickness=1
      - CornerRadius=10
  - target: Taskbar.TaskItemThumbnailView > Grid@CommonStates > Border#BackgroundBorder
    styles:
      - Background@PointerOver:=$HoverFill
      - CornerRadius=6
  - target: TextBlock#DisplayNameTextBlock
    styles:
      - Foreground:=$TextPrimary
      - FontSize=12
  - target: WindowsInternal.ComposableShell.Experiences.Switcher.AltTab > Grid#ModalRootGrid > Border#BackgroundElement
    styles:
      - Background=Transparent
      - BorderThickness=0
  - target: WindowsInternal.ComposableShell.Experiences.Switcher.AltTab > Grid#ModalRootGrid > Border#BackgroundElement > WindowsInternal.ComposableShell.Experiences.Switcher.SwitchItemList
    styles:
      - Background:=$MenuBarBackground
      - BorderBrush:=$MenuBarBorder
      - BorderThickness=1
      - CornerRadius=14
  - target: TextBlock#DisplayName
    styles:
      - Foreground:=$TextPrimary
  - target: Border#VirtualDesktopBarBackground
    styles:
      - Background:=$MenuBarBackground
      - BorderBrush:=$MenuBarBorder
      - BorderThickness=1
      - CornerRadius=10
  - target: WindowsInternal.ComposableShell.Experiences.Switcher.VirtualDesktopBarElement > Grid#GridElement > Border#VirtualDesktopSwitcherBackground
    styles:
      - Background:=$MenuBarBackground
      - BorderBrush:=$MenuBarBorder
      - BorderThickness=1
      - CornerRadius=10
  - target: Windows.UI.Xaml.Controls.Grid#ConfirmatorMainGrid
    styles:
      - Background:=$MenuBarBackground
      - BorderBrush:=$MenuBarBorder
      - BorderThickness=1
      - CornerRadius=14
      - RequestedTheme=2
  - target: Windows.UI.Xaml.Shapes.Rectangle#HorizontalTrackRect
    styles:
      - Fill=#33FFFFFF
      - RadiusX=7
      - RadiusY=7
      - Height=12
      - Margin=0
  - target: Windows.UI.Xaml.Shapes.Rectangle#HorizontalDecreaseRect
    styles:
      - Fill=$Accent
      - RadiusX=7
      - RadiusY=7
      - Height=12
  - target: Windows.UI.Xaml.Controls.TextBlock#volumeLevelText
    styles:
      - Foreground:=$TextPrimary
  - target: Windows.UI.Xaml.Controls.Border#SnapPickerBorder, Border#SnapBarBorder
    styles:
      - Background:=$MenuBarBackground
      - BorderBrush:=$MenuBarBorder
      - BorderThickness=1
      - CornerRadius=10
      - RequestedTheme=2
  - target: WindowsInternal.ComposableShell.Experiences.TextInput.Common.InputSwitcher > ContentControl > ContentPresenter > Grid
    styles:
      - Background:=$MenuBarBackground
      - BorderBrush:=$MenuBarBorder
      - BorderThickness=1
      - CornerRadius=10
  - target: WindowsInternal.ComposableShell.Experiences.TextInput.Common.InputSwitcher > ContentControl > ContentPresenter > Grid > Grid
    styles:
      - Background=Transparent
      - BorderBrush=Transparent
  - target: Grid
    styles:
      - RequestedTheme=2
themeResourceVariables:
  - MediumTaskbarButtonExtent=30
  - SmallTaskbarButtonExtent=30
```
</details>
