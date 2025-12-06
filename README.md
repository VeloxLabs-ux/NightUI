<p align="center">
  <img src="docs/nightui-clone/assets/icon.svg" width="120" height="120" alt="NightUI Logo">
</p>

<h1 align="center">NightUI</h1>

<p align="center">
  <strong>A fully modded Rayfield fork with custom themes, animations & more</strong>
</p>

<p align="center">
  <a href="#installation">Installation</a> •
  <a href="#features">Features</a> •
  <a href="#quick-start">Quick Start</a> •
  <a href="#themes">Themes</a> •
  <a href="#documentation">Documentation</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-1.68-blue?style=flat-square" alt="Version">
  <img src="https://img.shields.io/badge/lua-5.1+-purple?style=flat-square" alt="Lua">
  <img src="https://img.shields.io/github/license/VeloxLabs-ux/NightUI?style=flat-square" alt="License">
</p>

---

## ✨ Features

### 🎨 Theming
- **14 Built-in Themes** - Default, Dark, Ocean, Emerald, Rose, Amber, Midnight, Sunset, Neon, Cyberpunk, Ice, Blood, Galaxy, Aqua
- **Custom Themes** - Create your own themes with `NightUI:AddTheme()`
- **30+ Theme Properties** - Full control over every color in the UI
- **Runtime Theme Switching** - Change themes on the fly

### 🎬 Animations (Modded)
- **Custom Animation Presets** - HoverIn, HoverOut, Press, Release, ToggleSlide, SliderDrag
- **Staggered Animations** - Elements animate in sequence for a polished feel
- **Bounce Effects** - Toggle switches with spring physics
- **Micro-interactions** - Subtle feedback on every interaction

### 🧩 Components
- **Toggle** - Animated on/off switch with bounce effect
- **Slider** - Draggable with circular knob handle
- **Button** - Click feedback with accent bar
- **Dropdown** - Single or multiple selection
- **Input** - Text input with placeholder
- **Keybind** - Key detection with hold support
- **ColorPicker** - Full color selection
- **Label** - Text with optional icon
- **Paragraph** - Title + content block
- **Section** - Collapsible groups
- **Divider** - Visual separator

### 🔧 Advanced
- **Config Saving** - Auto-save user preferences with Flags
- **Key System** - Built-in key verification
- **Search** - Find elements across all tabs
- **Notifications** - Toast notifications with icons
- **Mobile Support** - Works on all devices
- **Multi-Window** - Create multiple windows (offset automatically)

## 📦 Installation

```lua
local NightUI = loadstring(game:HttpGet('https://raw.githubusercontent.com/VeloxLabs-ux/NightUI/main/rayfield.lua'))()
```

## 🚀 Quick Start

```lua
local NightUI = loadstring(game:HttpGet('https://raw.githubusercontent.com/VeloxLabs-ux/NightUI/main/rayfield.lua'))()

local Window = NightUI:CreateWindow({
    Name = "My Script Hub",
    LoadingTitle = "Loading...",
    LoadingSubtitle = "by YourName",
    Theme = "Ocean",
    Icon = "moon"
})

local MainTab = Window:CreateTab("Main", "home")

MainTab:CreateToggle({
    Name = "Enable Feature",
    CurrentValue = false,
    Flag = "FeatureToggle",
    Callback = function(Value)
        print("Toggle:", Value)
    end
})

MainTab:CreateSlider({
    Name = "Walk Speed",
    Range = {16, 500},
    Increment = 1,
    Suffix = " studs/s",
    CurrentValue = 16,
    Flag = "WalkSpeed",
    Callback = function(Value)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value
    end
})

MainTab:CreateButton({
    Name = "Click Me",
    Callback = function()
        print("Button clicked!")
    end
})
```

## 🎨 Themes

NightUI comes with 14 beautiful built-in themes:

| Theme | Background | Accent |
|-------|------------|--------|
| Default | Dark Gray | Blue |
| Dark | Navy | Blue |
| Ocean | Deep Blue | Cyan |
| Emerald | Forest | Green |
| Rose | Wine | Pink |
| Amber | Brown | Orange |
| Midnight | Purple | Violet |
| Sunset | Maroon | Orange |
| Neon | Black | Cyan |
| Cyberpunk | Black | Magenta |
| Ice | Navy | Light Blue |
| Blood | Dark Red | Red |
| Galaxy | Purple | Violet |
| Aqua | Teal | Cyan |

```lua
-- Set theme on creation
local Window = NightUI:CreateWindow({
    Name = "My UI",
    Theme = "Ocean"
})

-- Change theme at runtime
NightUI:ChangeTheme("Cyberpunk")
```

## 🎨 Custom Themes

Create your own theme with full control over 30+ color properties:

```lua
-- Register a custom theme
NightUI:AddTheme("MyTheme", {
    TextColor = Color3.fromRGB(255, 255, 255),
    Background = Color3.fromRGB(20, 20, 30),
    Topbar = Color3.fromRGB(30, 30, 45),
    Shadow = Color3.fromRGB(10, 10, 15),
    
    TabBackground = Color3.fromRGB(25, 25, 40),
    TabBackgroundSelected = Color3.fromRGB(100, 50, 200),
    TabTextColor = Color3.fromRGB(180, 180, 200),
    SelectedTabTextColor = Color3.fromRGB(255, 255, 255),
    
    ElementBackground = Color3.fromRGB(25, 25, 40),
    ElementBackgroundHover = Color3.fromRGB(35, 35, 55),
    ElementStroke = Color3.fromRGB(60, 60, 90),
    
    ToggleBackground = Color3.fromRGB(25, 25, 40),
    ToggleEnabled = Color3.fromRGB(100, 50, 200),
    ToggleDisabled = Color3.fromRGB(60, 60, 80),
    
    SliderBackground = Color3.fromRGB(60, 30, 120),
    SliderProgress = Color3.fromRGB(100, 50, 200),
    
    InputBackground = Color3.fromRGB(25, 25, 40),
    InputStroke = Color3.fromRGB(80, 80, 120),
    PlaceholderColor = Color3.fromRGB(120, 120, 150)
})

-- Use your custom theme
local Window = NightUI:CreateWindow({
    Name = "My UI",
    Theme = "MyTheme"
})

-- Get all available themes
local themes = NightUI:GetThemeNames()
```

### Theme Properties

| Property | Description |
|----------|-------------|
| `TextColor` | Main text color |
| `Background` | Window background |
| `Topbar` | Top bar background |
| `Shadow` | Shadow color |
| `TabBackground` | Unselected tab background |
| `TabBackgroundSelected` | Selected tab background |
| `TabTextColor` | Unselected tab text |
| `SelectedTabTextColor` | Selected tab text |
| `ElementBackground` | Component background |
| `ElementBackgroundHover` | Component hover state |
| `ElementStroke` | Component border |
| `ToggleBackground` | Toggle track background |
| `ToggleEnabled` | Toggle enabled color |
| `ToggleDisabled` | Toggle disabled color |
| `SliderBackground` | Slider track background |
| `SliderProgress` | Slider fill color |
| `InputBackground` | Input field background |
| `InputStroke` | Input field border |
| `PlaceholderColor` | Input placeholder text |

## 📚 Components

### Toggle
```lua
local Toggle = Tab:CreateToggle({
    Name = "Enable Feature",
    CurrentValue = false,
    Flag = "FeatureToggle",
    Callback = function(Value) end
})
Toggle:Set(true)
```

### Slider
```lua
local Slider = Tab:CreateSlider({
    Name = "Speed",
    Range = {0, 100},
    Increment = 1,
    Suffix = "%",
    CurrentValue = 50,
    Flag = "Speed",
    Callback = function(Value) end
})
Slider:Set(75)
```

### Button
```lua
local Button = Tab:CreateButton({
    Name = "Click Me",
    Callback = function() end
})
```

### Dropdown
```lua
local Dropdown = Tab:CreateDropdown({
    Name = "Select",
    Options = {"Option 1", "Option 2", "Option 3"},
    CurrentOption = {"Option 1"},
    MultipleOptions = false,
    Flag = "Selection",
    Callback = function(Option) end
})
Dropdown:Set({"Option 2"})
```

### Input
```lua
local Input = Tab:CreateInput({
    Name = "Username",
    PlaceholderText = "Enter text...",
    RemoveTextAfterFocusLost = false,
    Flag = "Username",
    Callback = function(Text) end
})
```

### Keybind
```lua
local Keybind = Tab:CreateKeybind({
    Name = "Toggle Key",
    CurrentKeybind = "K",
    HoldToInteract = false,
    Flag = "ToggleKey",
    Callback = function(Key) end
})
```

### Color Picker
```lua
local ColorPicker = Tab:CreateColorPicker({
    Name = "Color",
    Color = Color3.fromRGB(255, 0, 0),
    Flag = "Color",
    Callback = function(Color) end
})
```

### Notifications
```lua
NightUI:Notify({
    Title = "Success!",
    Content = "Action completed.",
    Duration = 5,
    Image = "check-circle"
})
```

## 🔐 Key System

```lua
local Window = NightUI:CreateWindow({
    Name = "Premium Script",
    KeySystem = true,
    KeySettings = {
        Title = "Key Required",
        Subtitle = "Enter your key",
        Note = "Get key from discord.gg/yourserver",
        FileName = "MyScriptKey",
        Key = {"KEY123", "KEY456"}
    }
})
```

## 💾 Config Saving

```lua
local Window = NightUI:CreateWindow({
    Name = "My Script",
    ConfigurationSaving = {
        Enabled = true,
        FileName = "MyConfig",
        FolderName = "NightUI"
    }
})

-- Elements with Flag property are automatically saved
Tab:CreateToggle({
    Name = "Auto Save",
    Flag = "AutoSave", -- This value will be saved
    Callback = function(v) end
})
```

## 📖 Documentation

Full documentation available at: [NightUI Docs](https://veloxlabs-ux.github.io/NightUI/)

## 🙏 Special Thanks

- **[Rayfield](https://github.com/SiriusSoftwareLtd/Rayfield)** - The original UI library that inspired NightUI
- **[Lucide Icons](https://lucide.dev)** - Beautiful open-source icons

## 📄 License

MIT License - feel free to use in your projects!

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/VeloxLabs-ux">VeloxLabs</a>
</p>
