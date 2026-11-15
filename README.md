# STIG-6

<#
.SYNOPSIS
    This PowerShell script forces Group Policy objects to process even if they have not changed.

.NOTES
    Author          : Htain Ney
    Date Created    : 2026-06-12
    Last Modified   : 2026-06-12
    Version         : 1.0
    CVEs            : N/A
    Plugin IDs      : N/A
    STIG-ID         : WN11-CC-000090

.TESTED ON
    Date(s) Tested  : 2026-11-14
    Tested By       : Htain Ney
    Systems Tested  : Windows 11
    PowerShell Ver. : 5.1

.USAGE
    PS C:\> .\STIG-ID-WN11-CC-000090.ps1
#>

$registryPath = "HKLM:\SOFTWARE\Policies\Microsoft\Windows\Group Policy\{35378EAC-683F-11D2-A89A-00C04FBBCFA2}"
$valueName = "NoGPOListChanges"
$valueData = 0

if (-not (Test-Path $registryPath)) { New-Item -Path $registryPath -Force }
Set-ItemProperty -Path $registryPath -Name $valueName -Value $valueData -Type DWord
Write-Host "Registry value '$valueName' set to '$valueData' at '$registryPath'."
