---
title: '&lt;Commands &gt; , élément (programme d’amorçage) | Microsoft Docs'
description: L’élément Commands implémente les tests dans les éléments sous InstallChecks et déclare le package à installer si le test du programme d’amorçage ClickOnce échoue.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f53ca683e40be8e3cc428d013d2b8d3c8c5773e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881228"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Commands &gt; , élément (programme d’amorçage)
L' `Commands` élément implémente les tests décrits par les éléments situés sous l' `InstallChecks` élément, et déclare le package que le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] programme d’amorçage doit installer en cas d’échec du test.

## <a name="syntax"></a>Syntaxe

```xml
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
 L’élément `Commands` est obligatoire. L’élément a l’attribut suivant.

|Attribut|Description|
|---------------|-----------------|
|`Reboot`|facultatif. Détermine si le système doit redémarrer si l’un des packages retourne un code de sortie de redémarrage. La liste suivante affiche les valeurs valides :<br /><br /> `Defer`. Le redémarrage est différé jusqu’à un moment ultérieur.<br /><br /> `Immediate`. Entraîne un redémarrage immédiat si l’un des packages a retourné un code de sortie de redémarrage.<br /><br /> `None`. Provoque l’ignorance des demandes de redémarrage.<br /><br /> Par défaut, il s’agit de `Immediate`.|

## <a name="command"></a>Commande
 L'élément `Command` est un élément enfant de l'élément `Commands`. Un `Commands` élément peut avoir un ou plusieurs `Command` éléments. L’élément a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`PackageFile`|Obligatoire. Nom du package à installer si une ou plusieurs des conditions spécifiées par `InstallConditions` retournent la valeur false. Le package doit être défini dans le même fichier à l’aide d’un `PackageFile` élément.|
|`Arguments`|Facultatif. Ensemble d’arguments de ligne de commande à passer dans le fichier de package.|
|`EstimatedInstallSeconds`|Facultatif. Durée estimée, en secondes, nécessaire à l’installation du package. Cette valeur détermine la taille de la barre de progression affichée par le programme d’amorçage à l’utilisateur. La valeur par défaut est 0, auquel cas aucune estimation de temps n’est spécifiée.|
|`EstimatedDiskBytes`|Facultatif. Quantité estimée d’espace disque, en octets, que le package occupera une fois l’installation terminée. Cette valeur est utilisée dans l’espace disque requis que le programme d’amorçage affiche à l’utilisateur. La valeur par défaut est 0. dans ce cas, le programme d’amorçage n’affiche pas d’espace disque requis.|
|`EstimatedTempBytes`|Facultatif. Quantité estimée d’espace disque temporaire, en octets, requis par le package.|
|`Log`|Facultatif. Chemin d’accès au fichier journal généré par le package, par rapport au répertoire racine du package.|

## <a name="installconditions"></a>InstallConditions
 L' `InstallConditions` élément est un enfant de l' `Command` élément. Chaque `Command` élément ne peut avoir qu’un seul `InstallConditions` élément. Si aucun `InstallConditions` élément n’existe, le package spécifié par `Condition` est toujours exécuté.

## <a name="bypassif"></a>BypassIf
 L' `BypassIf` élément est un enfant de l' `InstallConditions` élément et décrit une condition positive sous laquelle la commande ne doit pas être exécutée. Chaque `InstallConditions` élément peut avoir zéro ou plusieurs `BypassIf` éléments.

 `BypassIf` a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`Property`|Obligatoire. Nom de la propriété à tester. La propriété doit avoir été définie précédemment par un enfant de l' `InstallChecks` élément. Pour plus d’informations, consultez [ \<InstallChecks> élément](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Obligatoire. Type de comparaison à effectuer. La liste suivante affiche les valeurs valides :<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Obligatoire. Valeur à comparer à la propriété.|
|`Schedule`|Facultatif. Nom d’une `Schedule` balise qui définit le moment où cette règle doit être évaluée.|

## <a name="failif"></a>FailIf
 L' `FailIf` élément est un enfant de l' `InstallConditions` élément et décrit une condition positive sous laquelle l’installation doit s’arrêter. Chaque `InstallConditions` élément peut avoir zéro ou plusieurs `FailIf` éléments.

 `FailIf` a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`Property`|Obligatoire. Nom de la propriété à tester. La propriété doit avoir été définie précédemment par un enfant de l' `InstallChecks` élément. Pour plus d’informations, consultez [ \<InstallChecks> élément](../deployment/installchecks-element-bootstrapper.md).|
|`Compare`|Obligatoire. Type de comparaison à effectuer. La liste suivante affiche les valeurs valides :<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|
|`Value`|Obligatoire. Valeur à comparer à la propriété.|
|`String`|Facultatif. Texte à afficher à l’utilisateur en cas d’échec.|
|`Schedule`|Facultatif. Nom d’une `Schedule` balise qui définit le moment où cette règle doit être évaluée.|

## <a name="exitcodes"></a>ExitCodes
 L' `ExitCodes` élément est un enfant de l' `Command` élément. L' `ExitCodes` élément contient un ou plusieurs `ExitCode` éléments, qui déterminent ce que l’installation doit faire en réponse à un code de sortie d’un package. Il peut y avoir un `ExitCode` élément facultatif sous un `Command` élément. `ExitCodes` n’a pas d’attributs.

## <a name="exitcode"></a>ExitCode
 L' `ExitCode` élément est un enfant de l' `ExitCodes` élément. L' `ExitCode` élément détermine ce que l’installation doit faire en réponse à un code de sortie d’un package. `ExitCode` ne contient pas d’éléments enfants et a les attributs suivants.

|Attribut|Description|
|---------------|-----------------|
|`Value`|Obligatoire. Valeur de code de sortie à laquelle cet `ExitCode` élément s’applique.|
|`Result`|Obligatoire. Comment l’installation doit réagir à ce code de sortie. La liste suivante affiche les valeurs valides :<br /><br /> `Success`. Signale que le package est correctement installé.<br /><br /> `SuccessReboot`. Signale que le package est correctement installé et demande au système de redémarrer.<br /><br /> `Fail`. Signale le package comme ayant échoué.<br /><br /> `FailReboot`. Signale le package comme ayant échoué et demande au système de redémarrer.|
|`String`|Facultatif. Valeur à afficher à l’utilisateur en réponse à ce code de sortie.|
|`FormatMessageFromSystem`|Facultatif. Détermine s’il est possible d’utiliser le message d’erreur fourni par le système correspondant au code de sortie ou d’utiliser la valeur fournie dans `String` . Les valeurs valides sont `true` , ce qui signifie que utilise l’erreur fournie par le système, et `false` , ce qui signifie que utilise la chaîne fournie par `String` . Par défaut, il s’agit de `false`. Si cette propriété a `false` `String` la valeur, mais n’est pas définie, l’erreur fournie par le système est utilisée.|

## <a name="example"></a>Exemple
 L’exemple de code suivant définit des commandes pour installer le .NET Framework 2,0.

```xml
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
- [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)
- [\<InstallChecks> appartient](../deployment/installchecks-element-bootstrapper.md)