---
title: "&lt;Commands&gt;, &#233;l&#233;ment (programme d&#39;amor&#231;age) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Commands> (élément du programme d'amorçage)"
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# &lt;Commands&gt;, &#233;l&#233;ment (programme d&#39;amor&#231;age)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'élément `Commands` implémente les tests décrits par les éléments figurant sous l'élément `InstallChecks` et déclare le package que le programme d'amorçage [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] doit installer en cas d'échec du test.  
  
## Syntaxe  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## Éléments et attributs  
 L'élément `Commands` est obligatoire.  L'élément a l'attribut suivant.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Reboot`|Facultatif.  Détermine si le système doit redémarrer si l'un des packages retourne un code de sortie de redémarrage.  La liste suivante affiche les valeurs valides :<br /><br /> `Defer`.  Le redémarrage est différé à un moment ultérieur.<br /><br /> `Immediate`.  Entraîne un redémarrage immédiat si l'un des packages retourne un code de sortie de redémarrage.<br /><br /> `None`.  Toutes les demandes de redémarrage sont ignorées.<br /><br /> La valeur par défaut est `Immediate`.|  
  
## Commande  
 L'élément `Command` est un élément enfant de l'élément `Commands`.  Un élément `Commands` peut contenir un ou plusieurs éléments `Command`.  L'élément possède les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`PackageFile`|Obligatoire.  Nom du package à installer si une ou plusieurs conditions spécifiées par `InstallConditions` retournent la valeur false.  Le package doit être défini dans le même fichier à l'aide d'un élément `PackageFile`.|  
|`Arguments`|Facultatif.  Ensemble d'arguments de ligne de commande à passer dans le fichier de package.|  
|`EstimatedInstallSeconds`|Facultatif.  Temps estimé, en secondes, pour installer le package.  Cette valeur détermine la taille de la barre de progression affichée à l'utilisateur par le programme d'amorçage.  La valeur par défaut est 0 et, dans ce cas, aucune durée estimée n'est spécifiée.|  
|`EstimatedDiskBytes`|Facultatif.  Volume estimé d'espace disque, en octets, occupé par le package au terme de l'installation.  Cette valeur est utilisée dans les informations d'espace disque requis affichées à l'utilisateur par le programme d'amorçage.  La valeur par défaut est 0, auquel cas le programme d'amorçage n'affiche pas d'espace de disque dur requis.|  
|`EstimatedTempBytes`|Facultatif.  Volume estimé d'espace disque temporaire, en octets, nécessaire au package.|  
|`Log`|Facultatif.  Chemin d'accès au fichier journal généré par le package, relatif au répertoire racine du package.|  
  
## InstallConditions  
 L'élément `InstallConditions` est un enfant de l'élément `Command`.  Chaque élément `Command` ne peut avoir qu'un seul élément `InstallConditions`.  En l'absence d'un élément `InstallConditions`, le package spécifié par `Condition` s'exécute toujours.  
  
## BypassIf  
 L'élément `BypassIf` est un enfant de l'élément `InstallConditions`. Il décrit une condition positive en vertu de laquelle la commande ne doit pas être exécutée.  Chaque élément `InstallConditions` peut contenir zéro, un ou plusieurs éléments `BypassIf`.  
  
 `BypassIf` possède les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Property`|Obligatoire.  Nom de la propriété à tester.  La propriété doit avoir été définie précédemment par un enfant de l'élément `InstallChecks`.  Pour plus d'informations, consultez [\<InstallChecks\>, élément](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obligatoire.  Type de comparaison à exécuter.  La liste suivante affiche les valeurs valides :<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obligatoire.  Valeur à comparer à la propriété.|  
|`Schedule`|Facultatif.  Nom d'une balise `Schedule` qui définit le moment de l'évaluation de cette règle.|  
  
## FailIf  
 L'élément `FailIf` est un enfant de l'élément `InstallConditions` et décrit une condition positive sous laquelle l'installation doit s'arrêter.  Chaque élément `InstallConditions` peut contenir zéro, un ou plusieurs éléments `FailIf`.  
  
 `FailIf` possède les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Property`|Obligatoire.  Nom de la propriété à tester.  La propriété doit avoir été définie précédemment par un enfant de l'élément `InstallChecks`.  Pour plus d'informations, consultez [\<InstallChecks\>, élément](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obligatoire.  Type de comparaison à exécuter.  La liste suivante affiche les valeurs valides :<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obligatoire.  Valeur à comparer à la propriété.|  
|`String`|Facultatif.  Texte à afficher à l'utilisateur en cas d'échec.|  
|`Schedule`|Facultatif.  Nom d'une balise `Schedule` qui définit le moment de l'évaluation de cette règle.|  
  
## ExitCodes  
 L'élément `ExitCodes` est un enfant de l'élément `Command`.  L'élément `ExitCodes` contient un ou plusieurs éléments `ExitCode` qui déterminent ce que l'installation doit faire en réponse à un code de sortie émanant d'un package.  Il peut y avoir un élément `ExitCode` facultatif sous un élément `Command`.  `ExitCodes` ne possède aucun attribut.  
  
## ExitCode  
 L'élément `ExitCode` est un enfant de l'élément `ExitCodes`.  L'élément `ExitCode` détermine ce que l'installation doit faire en réponse à un code de sortie émanant d'un package.  `ExitCode` ne contient pas d'éléments enfants et a les attributs suivants.  
  
|Attribut|Description|  
|--------------|-----------------|  
|`Value`|Obligatoire.  Valeur du code de sortie applicable à cet élément `ExitCode`.|  
|`Result`|Obligatoire.  Réaction de l'installation face à ce code de sortie.  La liste suivante affiche les valeurs valides :<br /><br /> `Success`.  Indique que l'installation du package a réussi.<br /><br /> `SuccessReboot`.  Signale que l'installation du package a réussi et indique au système de redémarrer.<br /><br /> `Fail`.  Signale l'échec du package.<br /><br /> `FailReboot`.  Signale l'échec du package et indique au système de redémarrer.|  
|`String`|Facultatif.  Valeur à afficher à l'utilisateur en réponse à ce code de sortie.|  
|`FormatMessageFromSystem`|Facultatif.  Détermine s'il faut utiliser le message d'erreur fourni par le système correspondant au code de sortie ou utiliser la valeur fournie dans `String`.  Les valeurs valides sont `true` pour utiliser l'erreur fournie par le système et `false` pour utiliser la chaîne fournie par `String`.  La valeur par défaut est `false`.  Si cette propriété est `false`, mais que `String` n'est pas défini, l'erreur fournie par le système sera utilisée.|  
  
## Exemple  
 L'exemple de code suivant définit les commandes permettant d'installer le .NET Framework 2.0.  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## Voir aussi  
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks\>, élément](../deployment/installchecks-element-bootstrapper.md)