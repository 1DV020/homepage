##Introduction
For this module we will work with Active Directory and look at some of the concepts herein. After installing the A.D D.S role we start of by implementing an AGDLP strategy under certain parameters - the exact structure and naming convention will be up to you.

We will then setup group policies on these and assure that we have a proper delegation of control.

Lab memo will be found below

[Lab 4.pdf](https://github.com/1DV020/labs/raw/master/Lab%204/Lab_4.pdf)

If you somewhere get stuck and need directions for reading you can mail Maxim Kravchenko <mk223hm@student.lnu.se>, but try to be specific of what problem you are facing. You are also recommended to keep a well documented overview of the network and configuration files you have worked with.

## Deadline

You should present your solution at one of the lab session no later then 9/3 - 2018. The requirements will be tested. That includes restarting the machines to see that the changes you have made are persistent.


## Reference Demos
### Demo -  Install Active Directory
<iframe width="853" height="480" src="https://www.youtube.com/embed/klp6rsdwNLA?rel=0" frameborder="0" allowfullscreen></iframe>
* Add ADDS role
  ```
  Import-Module ServerManager
  Add-WindowsFeature AD-Domain-Services
  ```
* Set Administrator Password `net user administrator *`
* Promote DC
  ```
  Import-Module ADDSDeployment
  Install-ADDSForest `
  -CreateDnsDelegation:$false `
  -DatabasePath "C:\Windows\NTDS" `
  -DomainMode "Win2012R2" `
  -DomainName "corp.mediawork.com" `
  -DomainNetbiosName "MEDIAWORK" `
  -ForestMode "Win2012R2" `
  -InstallDns:$true `
  -LogPath "C:\Windows\NTDS" `
  -NoRebootOnCompletion:$false `
  -SysvolPath "C:\Windows\SYSVOL" `
  -Force:$true
  ```
