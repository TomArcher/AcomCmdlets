# AcomCmdlets
PowerShell cmdlets to work with ACOM MD files

**NOTE:** PowerShell is case insensitive. Capitalization used here for easier reading.

## Topics covered
- [Setting up your PowerShell environment](#setting-up-your-powershell-environment)
- [Using the AcomCmdlets](#using-the-acomcmdlets)
- [Getting help for syntax and examples](#getting-help-for-syntax-and-examples)

## Setting up your PowerShell environment
(All of these steps need to be done only the first time you use the cmdlets)

1. Copy all files from the Dist directory into the following directory:

  <YourLocalDocumentsFolder>\WindowsPowerShell\Modules\AcomCmdlets

2. Open the Windows PowerShell app as Administrator

3. Set the execution policy so that you can run the cmdlet. 

  PS> Set-ExecutionPolicy Unrestricted

4. Import the module containing the cmdlets

  PS> Import-Module AcomCmdlets

## Using the AcomCmdlets

The Get-AcomArticle cmdlet is used to parse the header information from ACOM MD files and return an object with all fields filled in.

You can then use standard Where-Object (where) and Sort-Object (sort) cmdlets to filter just the articles you want, and Select-Object (select) to see only the information you care about:

	PS> dir *.md | Get-AcomArticle | where author -eq "tarcher" | sort filename | select filename, pagetitle, pubdate

To make the cmdlet easier to use, parameters have been added to reduce typing.

- **-Author** allows you to filter based on author. The following produce the same results.

	    PS> dir *.md | Get-AcomArticle -author "tarcher" 
	
	    PS> dir *.md | Get-AcomArticle | where author -eq "tarcher"

- **-Stale** allows you to filter based on the article's pubdate being 90 days older than today's date. The following produce the same results.

    	PS> dir *.md | Get-AcomArticle -stale
    	
  	    PS> dir *.md | Get-AcomArticle | where { $_.pubdate.AddDays(90) -le [System.DateTime]::Now } 

- **-StaleWithin** allows you to filter based on when an article will go stale. For example, the following filters for all stale articles and articles that will be stale within 14 days:

    	PS> dir *.md | Get-AcomArticle -stalewithin 14
  	  
  	    PS> dir *.md | Get-AcomArticle | where { $_.pubdate.AddDays(76) -le [System.DateTime]::Now } 

## Getting help for syntax and examples
To get syntax help and to view examples of using the Get-AcomArticle cmdlet, use the Get-Help cmdlet as follows:

	PS> Get-Help Get-AcomArticle

	PS> Get-Help Get-AcomArticle -examples
	
