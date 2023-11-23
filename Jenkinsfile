pipeline
	{
	    agent any
		
	environment {
		EMAIL_RECIPIENT = 'nareshbijjamtest@gmail.com'
	}
	
	stages 
		{
		stage('Deploy Blueprism Artefacts') 
	{
			steps 
		{
				script 
				{
					withEnv ([
						"buildno=${env.BUILD_NUMBER}",
						"bpfilePath=${params.filePath}"
						]) {
						powershell '''
						#Deploy Blueprism Artefacts i.e. BusineTs Objects/Process exports, releases or JSON input for Envrinment Varibles
						Set-Location "C:\\Users\\Naresh Bijjam\\.jenkins\\"
						$currpath = Get-Location; Write-Host "Current Working directory: $currpath";
						
						$filename = "./"+"${env:bpfilePath}" ;Write-Host "File to be deployed: $filename"
						
						$automatec_exe = "C:\\Program Files\\Blue Prism Limited\\Blue Prism Automate\\Automatec.exe"
						
						#Deploy Blueprism release file
						if ((Test-Path -path $filename)) {
						#Deploy Blueprism release artifacts file (Blueprism Release Package, Process Export or Business Object Export)
						if ($filename. EndsWith(".bprelease") -or $filename. EndsWith(".bprelease`"") -or $filename. EndsWith(".bpprocess") -or
						$filename.EndsWith(".bpprocess`"") -or $filename.EndsWith(".bpobject") -or $filename.EndsWith(".bpobject`"")) {
						Write-Host "`nImporting Blueprism release package from... $filename"
						& $automatec_exe /importrelease "$filename" /overwrite /user admin ZAQ!zaq1 /dbconname LocalDB Connection
						}
						
					}
				'''	
				}
				}
			}
		}
	
		}
		
post {
		always {
			cleanWs()
		}
	}
}