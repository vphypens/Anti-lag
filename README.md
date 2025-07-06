-- 🛑 Anti Lag Xiaomi Note 12 (4GB RAM) 🛑
-- Feito pra rodar liso sem deixar teu jogo feio

local player = game.Players.LocalPlayer

local function antiLagXiaomi()
	for _, v in pairs(workspace:GetDescendants()) do
		if v:IsA("ParticleEmitter") or v:IsA("Trail") then
			v.Enabled = false -- desativa particles e trails em vez de destruir
		elseif v:IsA("Fire") or v:IsA("Smoke") then
			v.Enabled = false -- desativa fogo e fumaça
		elseif v:IsA("Explosion") then
			v:Destroy() -- remove explosões que lagam tudo
		end
	end

	-- Ajustes Lighting sem deixar o jogo feio
	for _, v in pairs(game.Lighting:GetChildren()) do
		if v:IsA("DepthOfFieldEffect") or v:IsA("SunRaysEffect") or v:IsA("BloomEffect") then
			v.Enabled = false -- desativa efeitos mais pesados
		end
	end

	-- Mantém ColorCorrection e Blur pra não ficar feio demais

	-- Ajustes gerais
	game.Lighting.GlobalShadows = false
	game.Lighting.FogEnd = 100000
	game.Lighting.WaterTransparency = 0.8
	game.Lighting.WaterReflectance = 0

	-- Reduz qualidade gráfica pro médio-baixo (pra não ficar feio nem pesado)
	pcall(function()
		settings().Rendering.QualityLevel = Enum.QualityLevel.Level03
	end)

	print("✅ [ANTI-LAG XIAOMI 4GB] Ativado com sucesso")
end

-- Executa automático ao entrar no jogo
antiLagXiaomi()
