<br />
<div align="center">
  <h3 align="center">thugsense User Interface</h3>

  <p align="center">
    A user interface that supports roblox script executor lua. 
    <br />
    <br />
    <a href="https://raw.githubusercontent.com/xanific1337/thugsense/refs/heads/main/example.lua">View Demo</a>
    &middot;
    <a href="https://discord.gg/Zk3wWmxEST">Report Bug</a>
    &middot;
    <a href="https://discord.gg/Zk3wWmxEST">Request Feature</a>
  </p>

  <div align="center">
    <img src="https://github.com/xanific1337/thugsense/blob/main/image.png?raw=true)" alt="thugsense preview" />
  </div>
</div>


## Getting Started

This will go through how to use the library in your executor.

### Prerequisites

This is how you import the library through the repository.

- Example:

  ```lua
  -- EXTRA INFO: You can modify this library its open source. The code is horrendous but have fun.
  -- In order to make configs of your own make the inactivity text your own text you want
  -- I may implement theming etc in the future if i come back to this.

  local library = loadstring(game:HttpGet("(https://raw.githubusercontent.com/xanific1337/thugsense/refs/heads/main/library.lua)"))()
  local flags = library.flags -- access flags from here.
  ```

### Elements

- Window

  ```lua
  local window = library:Window({
    name = "Example Window",
    size = UDim2.fromOffset(500, 650)
  })
  ```

- Page

  ```lua
  local page = window:Page({
    name = "Main Page",
    columns = 2,
    subtabs = true
  })
  ```

- SubPage

  ```lua
  local subpage = page:SubPage({
    icon = "rbxassetid://123456",
    columns = 2
  })
  ```

- Section

  ```lua
  local section = page:Section({
    name = "General Settings",
    side = 1
  })
  ```

- MultiSection

  ```lua
  local multisection = page:MultiSection({
    sections = {"Section A", "Section B"},
    side = 2
  })
  ```

- ScrollableSection

  ```lua
  local scroll = page:ScrollableSection({
    name = "Scrollable Area",
    side = 1,
    size = 250
  })
  ```

- Divider

  ```lua
  section:Divider()
  ```

- Label

  ```lua
  local lbl = section:Label({
    name = "Status: Ready",
    alignment = "Center"
  })
  ```

- Toggle

  ```lua
  section:Toggle({
    name = "Enable Feature",
    default = false,
    flag = "EnableFeature",
    callback = function(value)
      print("Toggle:", value)
    end
  })
  ```

- Button

  ```lua
  section:Button({
    name = "Click Me",
    callback = function()
      print("Button clicked!")
    end
  })
  ```

- Slider

  ```lua
  section:Slider({
    name = "Volume",
    min = 0,
    max = 100,
    decimals = 1,
    default = 50,
    suffix = "%",
    flag = "VolumeLevel",
    callback = function(value)
      print("Volume:", value)
    end
  })
  ```

- Textbox

  ```lua
  section:Textbox({
    name = "Username",
    default = "Player",
    placeholder = "Enter your name",
    flag = "Username",
    callback = function(text)
      print("Text:", text)
    end
  })
  ```

- Dropdown

  ```lua
  section:Dropdown({
    name = "Mode",
    items = {"Easy", "Normal", "Hard"},
    default = "Normal",
    flag = "GameMode",
    multi = false,
    callback = function(option)
      print("Selected:", option)
    end
  })
  ```

- Listbox

  ```lua
  section:Listbox({
    size = 120,
    items = {"Item1", "Item2", "Item3"},
    default = "Item2",
    multi = false,
    flag = "ListChoice",
    callback = function(option)
      print("Chosen:", option)
    end
  })
  ```

- Keybind (Label)

  ```lua
  section:Label({
    name = "Hotkey"
  }):Keybind({
    name = "Bind",
    mode = "Toggle", -- "Toggle", "Hold", etc.
    default = Enum.KeyCode.F,
    flag = "Hotkey",
    callback = function(active)
      print("Hotkey active:", active)
    end
  })
  ```

- Colorpicker (Label)

  ```lua
  section:Label({
    name = "Label Color"
  }):Colorpicker({
    name = "Pick a Color",
    default = Color3.new(1, 1, 1),
    alpha = true,
    flag = "LabelColor",
    callback = function(color, alpha)
      print("Color:", color, "Alpha:", alpha)
    end
  })
  ```

- Colorpicker (Toggle)

  ```lua
  section:Toggle({
    name = "Colored Toggle",
    default = true,
    flag = "ColoredToggle",
    callback = function(v) end
  }):Colorpicker({
    name = "Toggle Color",
    default = Color3.new(0, 1, 0),
    alpha = true,
    flag = "ToggleColor",
    callback = function(color, alpha)
      print("Toggle Color:", color, "Alpha:", alpha)
    end
  })
  ```

- Keybind (Toggle)

  ```lua
  section:Toggle({
    name = "Keybind Toggle",
    default = false,
    flag = "KeyToggle",
    callback = function(v) end
  }):Keybind({
    name = "Toggle Key",
    mode = "Hold",
    default = Enum.KeyCode.E,
    flag = "KeyToggleBind",
    callback = function(active)
      print("Keybind active:", active)
    end
  })
  ```

- Textbox (Sections alias)

  ```lua
  -- If your API exposes a Sections alias:
  sections:Textbox({
    name = "Alias Textbox",
    default = "Text",
    placeholder = "Type here",
    flag = "AliasTextbox",
    callback = function(text)
      print("Alias:", text)
    end
  })
  ```

- Watermark

  ```lua
  library:Watermark("My Watermark")
  ```

- Notification

  ```lua
  library:Notification("Hello World!", 5, Color3.new(1, 0, 0), { Icon = "rbxassetid://123456" })
  ```

- KeybindList

  ```lua
  library:KeybindList()
  ```
