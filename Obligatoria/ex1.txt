$oldName = hostname
$newName = Read-Host -Prompt 'Escriu el nou nom del equip'
$newName = $newName.ToUpper()
Write-Host "[+] Nom Antic: '$oldName'"
Write-Host "[+] Nom Nou: '$newName'"
Write-Host "[*] El servidor es reinciara en 10 segons"
Rename-Computer -NewName $newName
Start-Sleep -Seconds 10
Restart-Computer