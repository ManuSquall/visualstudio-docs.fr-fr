---
title: "&lt;Strings&gt;, &#233;l&#233;ment (programme d&#39;amor&#231;age) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.NoStringsForCulture"
  - "MSBuild.GenerateBootstrapper.ProductCultureNotFound"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Strings> (élément du programme d'amorçage)"
ms.assetid: d5ea3613-5fc9-4a11-bef3-46a01178bf60
caps.latest.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 4
---
# &lt;Strings&gt;, &#233;l&#233;ment (programme d&#39;amor&#231;age)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Définit des chaînes localisées pour des noms de produits, des noms de packages et des messages d'erreur d'installation.  
  
## Syntaxe  
  
```  
<Strings>  
    <String  
        Name  
    >  
    </String>  
</Strings>  
```  
  
## Éléments et attributs  
 L'élément `Strings` est un enfant de l'élément `Package`.  Il ne possède aucun attribut.  
  
## Chaîne  
 L'élément `String` est un enfant de l'élément `Strings`.  Un élément `Strings` peut contenir un ou plusieurs éléments `String`.  
  
 `String` possède l'attribut suivant.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Name`|Obligatoire.  Nom de la chaîne.|  
  
## Exemple  
 L'exemple de code suivant spécifie toutes les chaînes en anglais pour le programme d'installation du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
```  
<Strings>  
    <String Name="DisplayName">.NET Framework 2.0</String>  
    <String Name="Culture">en</String>  
    <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>  
    <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>  
    <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>  
    <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>  
    <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>  
    <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>  
    <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>  
    <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>  
    <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>  
    <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>  
    <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>  
    <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>  
</Strings>  
```  
  
## Voir aussi  
 [\<Package\>, élément](../deployment/package-element-bootstrapper.md)