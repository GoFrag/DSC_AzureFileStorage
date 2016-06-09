# DSC Extension for Creating and Mapping Azure File Storage in Azure VM
## MIT License 2016 / just a proof of concept


## sample DSC

Configuration Sample
{   
   param ($MachineName,$pfUserName,$pfPassword,$storageAccountName,$storageAccountKey)
   Import-DSCResource -ModuleName xAzureFileStorage
   
   Node $MachineName
   {   
	
		xAzureStorageInstaller CreateShare
		{
            		shareName="artbrut"
			storageName=$storageAccountName
	        
			storageKey=$storageAccountKey
	        
		}
		XDriveMapper MapDrive
		{
			shareName="artBrut"
			storageName=$storageAccountName
	        
			storageKey=$storageAccountKey
	        	DriveLetter="z:"
			DependsOn = "[xAzureStorageInstaller]CreateShare"
		}
    }

}


