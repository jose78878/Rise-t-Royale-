-- Criar ScreenGui
tela localGui = Instância.new("ScreenGui")
screenGui.Parent = jogo.CoreGui
telaGui.ResetOnSpawn = false

-- Crie o botão abrir/fechar no canto superior-direito
local toggleButton = Instance.new("Button Texto")
toggleButton.Parent = telaGui
botão de alternância.Tamanho = UDim2.new(0, 100, 0, 50)
toggleButton.Posição = UDim2.new(1, -110, 0, 10) - Canto superior-direito
toggleButton.Text = "Abrir"
toggleButton.BackgroundColor3 = Color3.new(0.2, 0.2, 0.2)
toggleButton.TextColor3 = Color3.new(1, 1, 1)

-- Crie a moldura para segurar os botões (Inicialmente invisível)
local frame = Instance.new("Moldura")
frame.Parent = telaGui
frame.Size = UDim2.new(0, 150, 0, 80) - Tamanho compacto do quadro
frame.Position = UDim2.new(0.5, -75, 0.5, -40)
frame.BackgroundTransparência = 0.5
frame.BackgroundColor3 = Color3.new(0.1, 0.1, 0.1)
frame.Visible = false -- Inicialmente escondido

-- Criar botão "Docks"
local docksButton = Instance.new("Button Texto")
docksButton.Parent = quadro
docksButton.Size = UDim2.new(0, 150, 0, 35) -- Tamanho menor do botão
docksButton.Position = UDim2.new(0, 0, 0, 0)
docksButton.Text = "Docks"
docksButton.BackgroundColor3 = Color3.new(0, 0,5, 0,8)
docksButton.TextColor3 = Color3.new(1, 1, 1)

-- Criar botão "Palace"
palácio localButton = Instance.new("Button do Texto")
palaceButton.Parent = quadro
palaceButton.Size = UDim2.new(0, 150, 0, 35) - Tamanho menor do botão
palaceButton.Position = UDim2.new(0, 0, 0, 40)
palaceButton.Text = "Palace"
palaceButton.BackgroundColor3 = Color3.new(0.8, 0.5, 0)
palaceButton.TextColor3 = Color3.new(1, 1, 1)

-- Teleportar locais
docas locaisPosição = Vector3.new(-184.79580688476562, 21.837919235229492, 540.3627319335938)
palácio localPosição = Vector3.new(-178.2334747314453, 42.46976089477539, 2044.0440673828125)

-- Função depurativa
depuração (mensagem) da função local
    print("DEBUG: ".. mensagem)
fim fim

-- Função para fazer o jogador pular e se teletransportar
função local teleportTo (localização)
    jogador local = game.Players.Jogador local
    personagem local = player.Character or player.CharacterAdicionado: Wait()
    humanoide local = personagem: WaitForChild("Humanoid")
    humanoid LocalRootPart = personagem: WaitForChild("HumanoidRootPart")
    
    -- Mensagem de depuração para iniciar o teleporte
    debug ("Fazendo o jogador pular antes de se teletransportar")
    
    -- Faça o jogador pular
    humanoid: ChangeState (Enum.HumanoidStateType.Jumping)
    
    -- Espere um breve momento para garantir os registros de salto
    aguarde(0.1)
    
    -- Eleve ligeiramente o local de teletransporte para evitar colisões com o solo
    local ajustadoLocalização = localização + Vector3.new(0, 5, 0)
    
    -- Use o PivotTo para teleporte confiável
    caractere: PivotTo (CFrame.new (localização ajustada))
    
    -- Depurando mensagem após teleporte
    debug("O jogador teletransportado para:".. tostring(adjustedLocation))
fim fim

-- Ações do clique do botão
docksButton.MouseButton1Clique em:Connect(function()
    debug ("Botão docks clicado")
    teleportPara (docksPosição)
fim)

palaceButton.MouseButton1Clique em:Connect(function()
    debug ("Botão Palace clicado")
    teleportTo (palacePosição)
fim)

-- Alterne a visibilidade do quadro com o botão abrir/fechar
toggleButton.MouseButton1Clique em:Connect(function()
    se frame.Visível então
        frame.Visible = false
        toggleButton.Text = "Abrir"
        debug ("Moldura fechada")
    else
        frame.Visible = true
        toggleButton.Text = "Fechar"
        debug ("Frame aberto")
    fim fim
fim)
