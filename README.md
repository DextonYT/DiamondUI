# Diamond UI Library
This documentation is for DiamondUI

## Booting the library
```lua
local Diamond = loadstring(game:HttpGet('https://pastebin.com/raw/Jh7cq2Vn'))()
```

## Creating A Window
```lua
local Window = Diamond:CreateWindow({
   Name = "DiamondUI Example Window",
   LoadingTitle = "Diamond UI",
   LoadingSubtitle = "by Dexton",
   ConfigurationSaving = {
      Enabled = true,
      FolderName = nil, -- Create a custom folder for your hub/game
      FileName = "Diamond"
   },
   Discord = {
      Enabled = false,
      Invite = "ABCD", -- The Discord invite code, do not include discord.gg/. EX: discord.gg/ABCD would be ABCD
      RememberJoins = true -- Set this to false to make them join the discord every time they load it up
   },
   KeySystem = false, -- Set this to true to use our key system
   KeySettings = {
      Title = "Untitled",
      Subtitle = "Key System",
      Note = "No method of obtaining the key is provided", -- This shows up when you have the key system enabled
      FileName = "Key", -- It is recommended to use something unique as other scripts using DextonUI may overwrite your key file
      SaveKey = true, -- The user's key will be saved, but if you change the key, they will be unable to use your script
      GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like ArrayField to get the key from for example, pastebin or github.
      Actions = {
            [1] = {
                Text = 'Click here to copy the key link <--',
                OnPress = function()
                    print('Pressed')
                end,
                }
            },
      Key = {"Hello"} -- List of keys that will be accepted by the system, can be RAW file links (pastebin, github etc) or simple strings ("hello","key22")
   }
})```

## Creating A Tab
```lua
local Tab = Window:CreateTab("Tab Example", 4483362458) -- Title, Image
```

## Creating a section
```lua
local Section = Tab:CreateSection("Section Example",false) -- The 2nd argument is to tell if its only a Title and doesnt contain element
```

## Updating a section
```lua
Section:Set("Section Example")

-- Coming soon (MAYBE)
Section:Destroy()
Section:Lock()
Section:Unlock()```

## Destroying the interface
```lua
ArrayField:Destroy()
```

## Notifying the user
```lua
Diamond:Notify({
   Title = "Notification Title",
   Content = "Notification Content",
   Duration = 6.5,
   Image = 4483362458,
   Actions = { -- Notification Buttons
      Ignore = {
         Name = "Okay!",
         Callback = function()
         print("The user tapped Okay!") -- function when okay is pressed
      end
   },
 },
})
```

## Creating A Button
```lua
local Button = Tab:CreateButton({
   Name = "Button Example", 
   Interact = 'Click',
   Callback = function()
   -- The function that takes place when the button is pressed
   end,
})
```

## Creating A Toggle
```lua
local Toggle = Tab:CreateToggle({
   Name = "Toggle Example",
   CurrentValue = false,
   Flag = "Toggle1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   -- The function that takes place when the toggle is pressed
   -- The variable (Value) is a boolean on whether the toggle is true or false
   end,
})
```

## Updating A Toggle
```lua
Toggle:Set(false)
```

## Creating a color picker
```lua
local ColorPicker = Tab:CreateColorPicker({
    Name = "Color Picker",
    Color = Color3.fromRGB(255,255,255),
    Flag = "ColorPicker1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
    Callback = function(Value)
        -- The function that takes place every time the color picker is moved/changed
        -- The variable (Value) is a Color3fromRGB value based on which color is selected
    end
})
```

## Updating a color picker
```lua
ColorPicker:Set(Color3.fromRGB(255,255,255))
```

## Creating a slider
```lua
local Slider = Tab:CreateSlider({
   Name = "Slider Example",
   Range = {0, 100},
   Increment = 10,
   Suffix = "Bananas",
   CurrentValue = 10,
   Flag = "Slider1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
   -- The function that takes place when the slider changes
   -- The variable (Value) is a number which correlates to the value the slider is currently at
   end,
})
```

## Updating a Slider
```lua
Slider:Set(10) -- The new slider integer value
```
## Creating an Adaptive Input Box (TEXTBOX)
```lua
local Input = Tab:CreateInput({
   Name = "Input Example",
   PlaceholderText = "Input Placeholder", -- text for when the textbox is empty
   NumbersOnly = true, -- If the user can only type numbers. Remove or set to false if none.
   CharacterLimit = 15, --max character limit. Remove or set to false
   OnEnter = true, -- Will callback only if the user pressed ENTER while being focused on the the box.
   RemoveTextAfterFocusLost = false, -- Speaks for itself.
   Callback = function(Text)
   -- The function that takes place when the input is changed
   -- The variable (Text) is a string for the value in the text box
   end,
})
```

## Creating a dropdown menu
```lua
local Dropdown = Tab:CreateDropdown({
   Name = "Dropdown Example",
   Options = {"Option 1","Option 2"},
   CurrentOption = "Option 1" or {"Option 1","Option 3"},
   MultiSelection = true, -- If MultiSelections is allowed
   Flag = "Dropdown1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Option)
   -- The function that takes place when the selected option is changed
   -- The variable (Option) is a string for the value that the dropdown was changed to
   end,
})
```

## Updating a dropdown menu
```lua
Dropdown:Set("Option 2" or <table>) -- The new option value

Dropdown:Refresh({<table>},<selecteds>)

Dropdown:Add('test')
Dropdown:Remove('test')
```

## General settings [For every element you can add these. (Optional)]
```lua
local ElementExample
ElementExample = Tab:Create______({

Info = {
   Image = '1234567890',
   Text = 'Description for the prompt'
},
SectionParent = Section -- Section it's parented to

})```

## Updating an existing element
```lua
Element:Destroy() -- Destroy

Element:Visible(<bool>)

Element:Lock(Reason:<string>) -- Lock
Element:Unlock()  -- Unlock
```

## Check the value of an existing element

To check the current value of an existing element, using the variable, you can do ElementName.CurrentValue, if it's a keybind or dropdown, you will need to use KeybindName.CurrentKeybind or DropdownName.CurrentOption You can also check it via the flags from You can also check it via the flags from Diamond.Flags


## Creating A Bind
```lua
local Keybind = Tab:CreateKeybind({
   Name = "Keybind Example",
   CurrentKeybind = "Q",
   HoldToInteract = false,
   Flag = "Keybind1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Keybind)
   -- The function that takes place when the keybind is pressed
   -- The variable (Keybind) is a boolean for whether the keybind is being held or not (HoldToInteract needs to be true)
   end,
})
```

## Updating a keybind
```lua
Keybind:Set("RightCtrl") -- Keybind (string)
```

## Creating a label
```lua
local Label = Tab:CreateLabel("Label Example")
```

## Updating a label
```lua
Label:Set("Label Example")
```

## Creating a paragraph
```lua
local Paragraph = Tab:CreateParagraph({Title = "Paragraph Example", Content = "Paragraph Example"})
```
## Updating a Paragraph
```lua
Paragraph:Set({Title = "Paragraph Example", Content = "Paragraph Example"})
```
