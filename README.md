-- Script Anti Lag Avançado ✦ Feito pelo ChatGPT Cearense

-- Limpa partículas, decals, textures, trails, smoke, fire, sparkles
for _,v in pairs(workspace:GetDescendants()) do
    if v:IsA("Part") or v:IsA("UnionOperation") or v:IsA("MeshPart") then
        v.Material = Enum.Material.SmoothPlastic
        v.Reflectance = 0
        if v.Transparency > 0.5 then
            v:Destroy() -- remove partes muito transparentes
        end
    elseif v:IsA("Decal") or v:IsA("Texture") then
        v:Destroy()
    elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
        v:Destroy()
    elseif v:IsA("Smoke") or v:IsA("Fire") or v:IsA("Sparkles") then
        v:Destroy()
    end
end

-- Desativa sombras globais e configura qualidade mínima
game.Lighting.GlobalShadows = false
game.Lighting.FogEnd = 100000000
game.Lighting.Brightness = 2

-- Remove efeitos do Lighting
for _,v in pairs(game.Lighting:GetChildren()) do
    if v:IsA("BlurEffect") or v:IsA("SunRaysEffect") or v:IsA("ColorCorrectionEffect")
    or v:IsA("BloomEffect") or v:IsA("DepthOfFieldEffect") then
        v:Destroy()
    end
end

-- Desativa Terrain Decals
workspace.Terrain.Decoration = false

-- Remove sons loopados sem importância
for _,v in pairs(workspace:GetDescendants()) do
    if v:IsA("Sound") then
        if v.Looped == true and v.IsPlaying == true then
            v:Stop()
        end
    end
end

-- Remove GUIs invisíveis que rodam scripts desnecessários
for _,v in pairs(game:GetDescendants()) do
    if v:IsA("ScreenGui") and v.Enabled == false then
        v:Destroy()
    end
end

print("✦ Anti Lag Avançado 100% ativado com sucesso, visse!")
