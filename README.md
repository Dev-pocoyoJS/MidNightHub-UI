# MidNight Hub — UI

Biblioteca de interface usada pelos scripts do MidNight Hub.

## Como carregar

```lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/Dev-pocoyoJS/MidNightHub-UI/main/midnight_lib.lua"))()

local Window = Library:CreateWindow({ Name = "MidNight Hub", SubName = "Notify" })
local Page = Window:AddPage({ Name = "Principal", Icon = "home" })
local Section = Page:AddSection({ Name = "Geral" })
```

## Campo de texto (Input)

Nome à esquerda e caixa de texto à direita, com uma linha embaixo que acende enquanto o campo está em uso.

```lua
local Key = Section:AddInput({
    Name = "Key",
    Placeholder = "Cole aqui a sua key",
    Default = "",
    Width = 0.56,        -- opcional: fração da linha ocupada pela caixa (0.2 a 0.9)
    Finished = true,     -- opcional: false chama o Callback a cada letra; true (padrão) só ao sair do campo
    Callback = function(text) print(text) end,
})

Key:Get()          -- texto atual
Key:Set("abc")     -- troca o texto
```

## Tamanho da UI

No canto de baixo, à esquerda da janela, fica o controle `-  100%  +`:

- `-` e `+` diminuem e aumentam a UI inteira em 10% (de 50% a 150%);
- clicar no número volta para 100%.

É o mesmo valor do controle "Tamanho da UI" da página Config, então fica salvo junto com as outras configurações.

```lua
Window:SetScale(1.2)                 -- 120%
Window:GetScale()                    -- valor atual
Window:SetScaleControlVisible(false) -- esconde o controle do canto
```

Para criar a janela já sem o controle: `Library:CreateWindow({ ..., ScaleControl = false })`.
