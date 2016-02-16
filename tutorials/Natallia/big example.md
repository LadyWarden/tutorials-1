---
title: # big example
description: big example
tags: tutorial:product/sapHana
---
Use Azure PowerShell to [task]
1.Go to https://account.hanatrial.ondemand.com and log in to your HCP cockpit.
This article shows you how to [task], using commands from both the Azure module and the Azure Resource Manager module. This is intended to help you learn the new commands as well as migrate existing scripts to the new commands.

## Prerequisite: Install a Recent Version of Azure PowerShell

If you haven't done so already, install at least the [version number] version of Azure PowerShell on your local computer. If you use an earlier version, it won't have the Azure Resource Manager cmdlets described in this article. For details, see:
 
- [How to install and configure Azure PowerShell](install-configure-powershell.md) for instructions on setting up Azure PowerShell.
- [Using Windows PowerShell with Resource Manager](powershell-azure-resource-manager.md) for basics on using Resource Manager.

> [AZURE.NOTE] Most tasks require you to use an administrator-level Azure PowerShell command prompt.

## Command Comparison

This [table | section] shows the command syntax.

These command examples use the following variables:

$FriendlyName"<Describe value>"

<!-- if it makes more sense to present this in a table, use this. Otherwise, delete. The table won't render until it's in Github or published to Sandbox.-->

Service Management | Resource Manager
---|----
`syntax` | `syntax`


<!--if it makes more sense to present this one command block after the other instead of a table, use this. Otherwise, delete-->
  
[Short intro sentence about the command. Omit if there's really nothing to say. But if it uses approaches such a the pipeline, explain that]:

	[command string]

## Script Examples

Here's an example that uses [cmdlet names)] to [task]. It includes commands that:

- [short verb, uses, has, is, etc]
- [next short verb] 

<!--include this statement if it uses variables that weren't introduced earlier--> It includes the following variables:

- [variable 1]
- [variable 2]

<!--This shows you how a recent example was presented as well as how it was formatted. Preceding each line with one tab or four spaces to format in a code block-->

	$family="Windows Server 2012 R2 Datacenter"
	$image=Get-AzureVMImage | where { $_.ImageFamily -eq $family } | sort PublishedDate -Descending | select -ExpandProperty ImageName -First 1
	$vmname="AZDC1"
	$vmsize="Medium"
	$vm1=New-AzureVMConfig -Name $vmname -InstanceSize $vmsize -ImageName $image
	
	$cred=Get-Credential -Message "Type the name and password of the local administrator account."
	$vm1 | Add-AzureProvisioningConfig -Windows -AdminUsername $cred.GetNetworkCredential().Username -Password $cred.GetNetworkCredential().Password
	
	$vm1 | Set-AzureSubnet -SubnetNames "BackEnd"
	
	$vm1 | Set-AzureStaticVNetIP -IPAddress 192.168.244.4
	
	$disksize=20
	$disklabel="DCData"
	$lun=0
	$hcaching="None"
	$vm1 | Add-AzureDataDisk -CreateNew -DiskSizeInGB $disksize -DiskLabel $disklabel -LUN $lun -HostCaching $hcaching
	
	$svcname="Azure-TailspinToys"
	$vnetname="AZDatacenter"
	New-AzureVM –ServiceName $svcname -VMs $vm1 -VNetName $vnetname


## Additional Resources
<!--At a minimum, include a link back to the migration task list article. Use the formats shown below. See create-links-markdown.md for more info -->
<!--use this format for links to other articles, such as the migration task list. -->
[Manage Availability](virtual-machines-manage-availability.md)

<!--To link to an ACOM page outside the /documentation/ subdomain (such as a pricing page, SLA page or anything else that is not a documentation article), use an absolute URL, but omit the locale:

    [link text](http://azure.microsoft.com/pricing/details/virtual-machines/)-->

<!--use this for URLs outside of ACOM. Be sure to locale, and if you're linking to the Azure library on MSDN, include the '/azure/' part of the URL-->
[Virtual machines documentation](https://msdn.microsoft.com/library/azure/jj156003.aspx)

