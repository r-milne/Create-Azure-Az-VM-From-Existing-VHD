.SYNOPSIS
	Purpose of this script to help Azure administrators with the process of reusing an existing VHD when creating an Azure VM. 

	This script uses the Azure Resource Manager model.  If you wish to use classic mode then this is not the script for you.  Heck, you can just do this in the classic management tool...

	This script is typically required when deleting an existing VM so that you can change properties that are only available at VM creation time.  

	For more details, please see this post:
		
	
	https://blog.rmilne.ca/**************************88 

	Refer to the blog post for all the details.
	


.DESCRIPTION
	Script will use the Azure AZ cmdlets to create a VM from an existing VHD file.  Previous version of this script used the older RM cmdlets.  They are no longer supported, hence the 	update to use AZ.
	
	This is useful since creating a VM from an existing old VHD is not currently possible in the Azure Portal.  Hence the script....
	
	This task can be driven by the need to change the Availability Set on a VM, which is currently set when creating the VM, and cannot be changed afterwards.  Bummer.
	 
	Depending upon your configuration, all the resources may be in the same resource group or they could be spread amongst multiple.  Adjust the entries as required.  One script does 	not fit all....

	You can either use an existing NIC or create a new one.  REM out the appropriate action.  By default a new one is create as I have no idea what nomenclature you used :) 

	You will need to edit the variables to fit your environment.  
		$ResourceGroupName		- Default resource group
		$Location			- Azure DC
		$VMName				- VM Name
		$OSDiskUri			- http path to the existing VHD
		$VMSize				- How big is this badboy going to be

		$SubnetName			- Name of Subnet
		$InterfaceName 			- NIC name.  If using existing NIC, match the name
		$VNetName 			- Network Name
		$VNetResourceGroupName 		- Resource Group where network resources live.  May be different than the other resources 

	

.VERSION
  
	1.0  03-04-2021 -- Initial script  Create-Azure-AZ-VM-Using-VHD-1.0 


  
This Sample Code is provided for the purpose of illustration only and is not intended to be used in a production environment.  
THIS SAMPLE CODE AND ANY RELATED INFORMATION ARE PROVIDED "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESSED OR IMPLIED, 
INCLUDING BUT NOT LIMITED TO THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A PARTICULAR PURPOSE.  
We grant You a nonexclusive, royalty-free right to use and modify the Sample Code and to reproduce and distribute the object code form of the Sample Code, 
provided that You agree: 
(i) to not use Our name, logo, or trademarks to market Your software product in which the Sample Code is embedded; 
(ii) to include a valid copyright notice on Your software product in which the Sample Code is embedded; and 
(iii) to indemnify, hold harmless, and defend Us and Our suppliers from and against any claims or lawsuits, including attorneys’ fees, that arise or result from the use or distribution of the Sample Code.
Please note: None of the conditions outlined in the disclaimer above will supercede the terms and conditions contained within the Premier Customer Services Description.
This posting is provided "AS IS" with no warranties, and confers no rights. 

Use of included script samples are subject to the terms specified at http://www.microsoft.com/info/cpyright.htm.
