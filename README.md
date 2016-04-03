# AcomCmdlets
PowerShell cmdlets to work with ACOM MD files

**NOTE:** PowerShell is case insensitive. Capitalization used here for easier reading.

## Topics covered
- [Setting up your PowerShell environment](#setting-up-your-powershell-environment)
- [Getting help for syntax and examples](#getting-help-for-syntax-and-examples)

## Setting up your PowerShell environment
(All of these steps need to be done only the first time you use the cmdlets)

1. Copy all files from the Dist directory into the following directory:

  &lt;YourLocalDocumentsFolder>\WindowsPowerShell\Modules\AcomCmdlets

1. Right-click each file and select the **Properties** context menu. From the **General** tab, select **Unblock**.

1. Open the Windows PowerShell app as Administrator

1. Set the execution policy so that you can run the cmdlet. 

  PS> Set-ExecutionPolicy Unrestricted

1. Import the module containing the cmdlets

  PS> Import-Module AcomCmdlets

## Getting help for syntax and examples
To get syntax help and to view examples of using the Get-AcomArticle cmdlet, use the Get-Help cmdlet as follows:

	PS> Get-Help Get-AcomArticle

	PS> Get-Help Get-AcomArticle -examples
	
