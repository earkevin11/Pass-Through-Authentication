# Pass-Through-Authentication
- Authentication goes to the local Active Directory before the Azure AD.

# Why is there Pass-Through Authentication?
- Some AD features are not present in Azure AD.
- Security organizations may have their own password policies in place and want users to authenticate against local AD before accessing Azure AD resources.

# How to enable Pass-Through Authentication?
- Start up AD Connect > Configure > Change user-sign in > select Pass-Through Authentication > enter credentials for domain administrator

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/168647551-518406bb-0027-4af4-bc2c-6ada71486a7a.png" height="75%" width="75%" alt="AD DS "/>
  
<p/>

- Select Pass-Through Authentication

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/168647876-8e56ac04-6754-496f-be06-24b4757ab479.png" height="75%" width="75%" alt="AD DS "/>
  
<p/>

- Click configure and ensure configuration was complete
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/168648011-72c4cd5b-10f3-4e49-a3b1-b0904e61832e.png" height="75%" width="75%" alt="AD DS "/>
  
<p/>


# One more step: Go backto AD connect > Configure > Customize Sycnhronization options > enter credentials > disable Password Hash Synchronization
- We do this because if we enabled Passthrough Authentication and have Password Hash Synchronization enabled, it will automatically use Password Hash Sychronization
- We want Pass-Through
<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/168648765-847f26d7-d573-4f8d-ae8f-3fdafb2e4966.png" height="75%" width="75%" alt="AD DS "/>
  
<p/>

# Test out by configure Active Directory user sign-in settings in onpremad enviroment. 
- Disable sign-in for all days and test out sign in
- This feature is not available in Azure AD
- Note that whatever settings an IT admin applied for sign-ins does not apply since it is Pass-Through Authentication (On-Prem first)

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/168650185-b09fdc7c-ebff-40c6-aac3-6c75ad47ce94.png" height="150%" width="150%" alt="AD DS "/>
  
<p/>

- Domainuser B failed sign-in

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/168652519-20dfab53-b5d6-4f30-a744-ffd31a335f28.png" height="60%" width="60%" alt="sign in "/>
  
<p/>

- Due to configuring log-in denies for all days. There will be an error message.
- This happens because authentication is occuring at the local on-prem Active Directory first.

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/168652730-a25edcd0-7031-48ec-b99c-c7b0e4de5bda.png" height="60%" width="60%" alt="error message"/>
  
<p/>



