# Fluent Ui Library 

## Inicialização da Library
```lua
local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()
--//
```


## Criando uma Window / Janela
```lua
local Window = Fluent:CreateWindow({
    Title = "Gay Hub", --Título do seu Hub
    SubTitle = "by Gay Productions",--sub título do seu Hub
    TabWidth = 160,
    Size = UDim2.fromOffset(560, 350),--Largura e Estatura do seu hub / Tamanho.
    Acrylic = true, --Blur
    Theme = "Darker",--Temas da cor: [ Dark, Darker, White, Rose, Aqua, Amethyst.
    MinimizeKey = Enum.KeyCode.LeftControl --Key para minimizar o seu hub
})
--//
```


## Criando Tabelas / Tab
 Lembrando: Os emojis das tabs podem ser achados ou escolidos no site: https://lucide.dev/icons
 !!!
 ```lua
--Fluent provides Lucide Icons https://lucide.dev/icons/ for the tabs, icons are optional
local Tabs = {
    Main = Window:AddTab({ Title = "Main", Icon = "cloud" }),
    Settings = Window:AddTab({ Title = "Settings", Icon = "settings" })
}
--[[
Main = Window:AddTab({ Title = "Main", Icon = "cloud" }),
Main = -- Nome da tab
Title = "Main", -- Título da tab
Icon = "cloud" --ícone
]]
--//
```


## Notificações
```lua
Fluent:Notify({
        Title = "Notificação", --Título da notificação
        Content = "Conteúdo", --Conteúdo da notificação
        SubContent = "Sub Conteúdo", --Sub Conteúdo da notificação
        Duration = 5 -- Duração da notificação (altere para nil, para a notificação ter a duração infinita.) 
    })
--//
```



## Parágrafos / Diálogos
```lua
 Tabs.Main:AddParagraph({
        Title = "Parágrafo", --Título do Parágrafo
        Content = "Conteúdo" --Conteúdo do Parágrafo.
    })
--//
```


## Botão com diálogo
```lua
 Tabs.Main:AddButton({
        Title = "Button",--Título do botão
        Description = "Botão", --Descrição do botão
        Callback = function()
            Window:Dialog({
                Title = "Title", --Título do diálogo
                Content = "Lol", --Conteúdo do diálogo
                Buttons = {
                    {
                        Title = "Yes",--Título do botão de confirmar
                        Callback = function()
                        --Função
                            print("yes sirrr") 
                        end
                    },
                    {
                        Title = "Cancel",--Título do botão de cancelar
                        Callback = function()
                           --função ou não.
                            print("Cancelled the dialog.")
                        end
                    }
                }
            })
        end
    })
--//
```



## Botão sem diálogo
```lua
 Tabs.Main:AddButton({
        Title = "Button",--título do botão
        Description = "Button Gay",--Descrição do botão
        Callback = function()
            --função
        end
    })
--//
```


## Toggle / Botão de ativar e desativar
```lua
local Toggle = Tabs.Main:AddToggle("MyToggle", {Title = "Toggle", Default = false })

    Toggle:OnChanged(function()
    --função do toggle
        print("Toggle changed:", Options.MyToggle.Value)
    end)

    Options.MyToggle:SetValue(false)
--[[
Title = "Toggle", -- Título do botão
Default = false }) -- Valor booleano ( true / false) 
]]
--//
```


## Slider / Controle deslizante
```lua
local Slider = Tabs.Main:AddSlider("Slider", {
        Title = "Slider", --Título do Slider
        Description = "This", --Descrição do slider
        Default = 2, --valor padrão
        Min = 0, --valor mínimo
        Max = 5, --valor máximo
        Rounding = 1,
        Callback = function(Value)
        --função
            print("Slider was changed:", Value)
        end
    })
--//
```
  

## Dropdowns
```lua
local Dropdown = Tabs.Main:AddDropdown("Dropdown", {
        Title = "Dropdown", --Título do dropdown
        Values = {"one", "two", "three", "four", "five", "six", "seven", "eight", "nine", "ten", "eleven", "twelve", "thirteen", "fourteen"},--Valores
        Multi = false, --Multi valor ( booleano) true / false
        Default = 1, --Valor Padrão
    })
--//
```


## ColorPicker
```lua
local Colorpicker = Tabs.Main:AddColorpicker("Colorpicker", {
        Title = "Colorpicker",--Título do ColorPicker
        Default = Color3.fromRGB(96, 205, 255) --Valor de cor padrão RGB
    })

    Colorpicker:OnChanged(function()
    --função
        print("Colorpicker changed:", Colorpicker.Value)
    end)
--//
```



## KeyBind
```lua
local Keybind = Tabs.Main:AddKeybind("Keybind", {
        Title = "KeyBind",
        Mode = "Toggle", -- Always, Toggle, Hold
        Default = "LeftControl", -- String as the name of the keybind (MB1, MB2 for mouse buttons)

        -- Occurs when the keybind is clicked, Value is `true`/`false`
        Callback = function(Value)
            print("Keybind clicked!", Value)
        end,

        -- Occurs when the keybind itself is changed, `New` is a KeyCode Enum OR a UserInputType Enum
        ChangedCallback = function(New)
            print("Keybind changed!", New)
        end
    })
--//
```


## Input texto
```lua
 local Input = Tabs.Main:AddInput("Input", {
        Title = "Input",--Título do input
        Default = "Default",--valor padrão do input
        Placeholder = "Placeholder",--texto que fica dentro do input
        Numeric = false, -- Only allows numbers
        Finished = false, -- Only calls callback when you press enter
        Callback = function(Value)
        --funções
            print("Input changed:", Value)
        end
    })
--//
```