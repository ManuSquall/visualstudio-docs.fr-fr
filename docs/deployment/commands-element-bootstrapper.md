---
title: '&lt;Commandes&gt; élément (programme d’amorçage) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 9d886d7fa7ea2ab6cb8c04810ab404a29898cd02
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Commandes&gt; élément (programme d’amorçage)
Le `Commands` élément implémente les tests décrits par les éléments figurant sous le `InstallChecks` élément et déclare le package que le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] programme d’amorçage doit installer si le test échoue.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le `Commands` élément est requis. L’élément a l’attribut suivant.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Reboot`|Facultatif. Détermine si le système doit redémarrer si aucun des packages retourne un code de sortie de redémarrage. La liste suivante indique les valeurs valides :<br /><br /> `Defer`. Le redémarrage est différé jusqu'à une date ultérieure.<br /><br /> `Immediate`. Entraîne un redémarrage immédiat si un des packages a retourné un code de sortie de redémarrage.<br /><br /> `None`. Fait toutes les demandes de redémarrage doivent être ignorés.<br /><br /> La valeur par défaut est `Immediate`.|  
  
## <a name="command"></a>Commande  
 L'élément `Command` est un élément enfant de l'élément `Commands`. A `Commands` élément peut avoir un ou plusieurs `Command` éléments. L’élément a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`PackageFile`|Obligatoire. Nom du package à installer si une ou plusieurs des conditions spécifiées par `InstallConditions` renvoient la valeur false. Le package doit être défini dans le même fichier en utilisant un `PackageFile` élément.|  
|`Arguments`|Facultatif. Un jeu d’arguments de ligne de commande à passer dans le fichier de package.|  
|`EstimatedInstallSeconds`|Facultatif. Le temps estimé, en secondes, nécessaire à installer le package. Cette valeur détermine la taille de la barre de progression qu'affiche par le programme d’amorçage pour l’utilisateur. La valeur par défaut est 0, auquel cas, aucune durée estimée est spécifiée.|  
|`EstimatedDiskBytes`|Facultatif. Estimation de la quantité d’espace disque, en octets, que le package occupera après l’installation est terminée. Cette valeur est utilisée dans l’espace disque nécessaire que le programme d’amorçage affiche à l’utilisateur. La valeur par défaut est 0, dans lequel le programme d’amorçage de cas n’affiche pas tout l’espace disque nécessaire.|  
|`EstimatedTempBytes`|Facultatif. Estimation de la quantité d’espace disque temporaire, en octets, ce qui nécessite le package.|  
|`Log`|Facultatif. Le chemin d’accès au fichier journal généré par le package, relatif au répertoire racine du package.|  
  
## <a name="installconditions"></a>InstallConditions  
 Le `InstallConditions` élément est un enfant de le `Command` élément. Chaque `Command` élément peut avoir au plus un `InstallConditions` élément. Si aucun `InstallConditions` élément existe, le package spécifié par `Condition` sera toujours exécuté.  
  
## <a name="bypassif"></a>BypassIf  
 Le `BypassIf` élément est un enfant de le `InstallConditions` élément et décrit une condition positive sous lequel la commande ne doit pas être exécutée. Chaque `InstallConditions` élément peut avoir zéro ou plusieurs `BypassIf` éléments.  
  
 `BypassIf` a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Property`|Obligatoire. Le nom de la propriété à tester. La propriété doit avoir été définie précédemment par un enfant de le `InstallChecks` élément. Pour plus d’informations, consultez [ \<InstallChecks > élément](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obligatoire. Le type de comparaison à effectuer. La liste suivante indique les valeurs valides :<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obligatoire. La valeur à comparer avec la propriété.|  
|`Schedule`|Facultatif. Le nom d’un `Schedule` balise qui définit quand cette règle doit être évaluée.|  
  
## <a name="failif"></a>FailIf  
 Le `FailIf` élément est un enfant de le `InstallConditions` élément et décrit une condition positive sous laquelle l’installation doit s’arrêter. Chaque `InstallConditions` élément peut avoir zéro ou plusieurs `FailIf` éléments.  
  
 `FailIf` a les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Property`|Obligatoire. Le nom de la propriété à tester. La propriété doit avoir été définie précédemment par un enfant de le `InstallChecks` élément. Pour plus d’informations, consultez [ \<InstallChecks > élément](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obligatoire. Le type de comparaison à effectuer. La liste suivante indique les valeurs valides :<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obligatoire. La valeur à comparer avec la propriété.|  
|`String`|Facultatif. Texte à afficher à l’utilisateur en cas d’échec.|  
|`Schedule`|Facultatif. Le nom d’un `Schedule` balise qui définit quand cette règle doit être évaluée.|  
  
## <a name="exitcodes"></a>ExitCodes  
 Le `ExitCodes` élément est un enfant de le `Command` élément. Le `ExitCodes` élément contient un ou plusieurs `ExitCode` éléments qui déterminent ce que l’installation doit faire en réponse à un code de sortie à partir d’un package. Il peut y avoir une option `ExitCode` élément sous un `Command` élément. `ExitCodes` Possède pas d’attributs.  
  
## <a name="exitcode"></a>Code de sortie  
 Le `ExitCode` élément est un enfant de le `ExitCodes` élément. Le `ExitCode` détermine ce que l’installation doit faire en réponse à un code de sortie à partir d’un package. `ExitCode` ne contient aucun élément enfant et possède les attributs suivants.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`Value`|Obligatoire. La valeur du code de sortie auquel ce `ExitCode` élément s’applique.|  
|`Result`|Obligatoire. Manière dont l’installation doit réagir à ce code de sortie. La liste suivante indique les valeurs valides :<br /><br /> `Success`. Marque le package a réussi.<br /><br /> `SuccessReboot`. Marque le package a réussi et fait en sorte que le redémarrage du système.<br /><br /> `Fail`. Signale le package a échoué.<br /><br /> `FailReboot`. Marque le package comme ayant échoué et fait en sorte que le redémarrage du système.|  
|`String`|Facultatif. La valeur à afficher à l’utilisateur en réponse à ce code de sortie.|  
|`FormatMessageFromSystem`|Facultatif. Détermine s’il faut utiliser le message d’erreur fournie par le système correspondant au code de sortie, ou utiliser la valeur fournie dans `String`. Les valeurs valides sont `true`, ce qui signifie que l’erreur fournie par le système, et `false`, ce qui signifie que la chaîne fournie par `String`. La valeur par défaut est `false`. Si cette propriété est `false`, mais `String` n’est pas défini, l’erreur fournie par le système sera utilisé.|  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant définit des commandes pour l’installation de .NET Framework 2.0.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma de Package et de produit](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks > élément](../deployment/installchecks-element-bootstrapper.md)