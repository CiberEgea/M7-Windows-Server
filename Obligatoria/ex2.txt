Clear-Host
$separador = "_"*55
$descripcion = Get-NetAdapter | select -ExpandProperty InterfaceDescription
$identificador = Get-NetAdapter | select -ExpandProperty ifIndex
$oldip = Get-NetIPAddress -AddressFamily IPv4 | where InterfaceIndex -eq $identificador| Select-Object -ExpandProperty IPAddress
Write-Host $separador
Write-Host "Configuracion de red Actual"
Write-Host $separador
Write-Host "Descripcion    | $descripcion"
Write-Host "Identificador  | $identificador"
Write-Host "Ip Actual      | $oldip"
Write-Host $separador
$newip = Read-Host -Prompt "Indique la nueva Ip"
$mascara = Read-Host -Prompt "Indique la Mascara de subred (1/32)"
$gateway = Read-Host -Prompt "Indique la puerta de enlace"
Write-Host $separador
#New-NetIPAddress -IPAddress $newip -PrefixLength $mascara -DefaultGateway $gateway -InterfaceIndex $identificador
Write-Host "`n"
$separador
Write-Host "Nueva Configuracion de Red"
$separador
Write-Host "Ip Antigua            | $oldip"
Write-Host "Ip Nueva              | $newip"
Write-Host "Mascara de subred     | $mascara"
Write-Host "Puerta de Enlace      | $gateway"
Write-Host $separador
Write-Host "`n"
Write-Host $separador
Write-Host "Test de conexion a Internet"
Write-Host $separador
if(Test-Connection www.google.es -Quiet) {Write-Output "Hay conexion a Internet"}
else {Write-Output "No hay conexion a Internet"}