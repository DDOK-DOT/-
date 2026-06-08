# -$token = "YOUR_GITHUB_TOKEN"
$body = @{
    name = "虾塘"
    description = ""
    private = $true
    auto_init = $false
} | ConvertTo-Json

irm "https://api.github.com/user/repos" -Method Post `
    -Headers @{
        "Authorization" = "Bearer $token"
        "X-GitHub-Api-Version" = "2022-11-28"
        "Accept" = "application/vnd.github+json"
    } `
    -ContentType "application/json" `
    -Body $body
