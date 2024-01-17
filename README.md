Simple Powershell Logging Functions

# Installation
Add the LoggingFunctions folder to your Powershell Modules Repository!<br>
Default Path for Windows = "C:\Program Files\WindowsPowerShell\Modules"

# Example of log
2024-01-17 09:32:04.096 - USER: myuser - GET - Retrieving data<br>
2024-01-17 09:32:04.306 - USER: myuser - WARNING - You ran into an error when trying to: Retrieving data<br>
2024-01-17 09:32:04.317 - USER: myuser - ERROR - The remote server returned an error: (403) Forbidden.

# How to use example
These logging functions will create a Logs folder if it does no already exist in your root directory!

## Normal log
```
Write-Log -Type UPDATE -Message "Updating user catalog" -Active $True
```

## If you only want to add a LineBreak
```
Write-Log -LineBreak -Active $True
```

## This log function can be used when running external retrievals, pushes or changes and you will recieve a log if something goes wrong.
```
Invoke-TryCatchLog -InfoLog "Retrieving users from Graph API" -LogToFile $True -ScriptBlock {
    Invoke-RestMethod -Method GET -Uri "GraphAPIEndPoint" -Headers $graphAuthenticationHeader
}
```
