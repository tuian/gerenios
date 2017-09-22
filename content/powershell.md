+++
title = "PowerShell"
date = "2017-09-22"
menu = "main"
tags = ["Office365", "PowerShell"]
categories = ["article"]
description = "How to connect to Office 365 with PowerShell"
thumbnail = "/images/PowerShell.png"
+++

This article explains how to connect Office 365 using PowerShell and more!
 <!--more-->
 
# How to connect to Office 365

## Preparation

Before you can use any Office 365 PowerShell cmdlets, you need to download and install them.

First you should save your credentials and tenant name to variables so you can use them later:
{{< highlight powershell >}}
$cred=Get-Credential
$tenant="yourtenant"
{{< /highlight>}}

## Office 365 (v1)

To connect to Office 365, please use the following command:
{{< highlight powershell >}}
Connect-MsolService -credential $credential
{{< /highlight>}}

## SharePoint Online

To connect to SharePoint online, please use the following command:
{{< highlight powershell >}}
Connect-SPOService -Url https://$tenant-admin.sharepoint.com -Credential $cred
{{< /highlight>}}

## Skype for Business

To connect to Skype for Business, please use the following command:
{{< highlight powershell >}}
$s4bses = New-CsOnlineSession -Credential $cred
Import-PSSession $s4bses
{{< /highlight>}}

## Exchange Online
To connect to Skype for Business, please use the following command:
{{< highlight powershell >}}
$exses = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $cred -Authentication Basic -AllowRedirection
Import-PSSession $exses
{{< /highlight>}}


