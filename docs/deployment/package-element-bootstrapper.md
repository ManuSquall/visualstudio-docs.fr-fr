---
title: '&lt;Package &gt; , élément (programme d’amorçage) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <package> element [bootstrapper]
ms.assetid: ecd06658-ad02-4440-bccd-88437b7fb816
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab3478f701cade458ffdb97caf4541a88f52230e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66745758"
---
# <a name="ltpackagegt-element-bootstrapper"></a>&lt;Package &gt; , élément (programme d’amorçage)
L' `Package` élément est l’élément XML de niveau supérieur à l’intérieur d’un fichier de package.

## <a name="syntax"></a>Syntaxe

```xml
<Package
    Culture
    Name
    LicenseAgreement
>
    <InstallChecks>
        <AssemblyCheck
            Property
            Name
            PublicKeyToken
            Version
            Language
            ProcessorArchitecture
        />
        <RegistryCheck
            Property
            Key
            Value
        />
        <ExternalCheck
            PackageFile
            Property
            Arguments
            Log
        />
        <FileCheck
            Property
            FileName
            SearchPath
            SpecialFolder
            SearchDepth
        />
        <MsiProductCheck
            Property
            Product
            Feature
        />
        <RegistryFileCheck
            Property
            Key
            Value
            File
            SearchDepth
        />
    </InstallChecks>

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

    <PackageFiles
        CopyAllComponents
    >
        <PackageFile
            Name
            Path
            HomeSite
            PublicKey
        />
    </PackageFiles>

    <Strings>
        <String
            Name
        >
        </String>
    </Strings>

    <Schedules>
        <Schedule
            Name
        >
           <BuildList />
           <BeforePackage />
           <AfterPackage />
        </Schedule>
    </Schedules>
</Package>
```

## <a name="elements-and-attributes"></a>Éléments et attributs
 L’élément `Package` est obligatoire. Il a les attributs suivants.

| Attribut | Description |
|--------------------| - |
| `Culture` | Obligatoire. Définit la culture pour ce package, qui détermine la langue à utiliser. Cet attribut est une clé de l' `Strings` élément, qui répertorie les chaînes spécifiques à la culture pour les noms de produits et les messages d’erreur pendant l’installation. |
| `Name` | Obligatoire. Nom du package affiché au développeur dans un outil tel que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Cet attribut est une clé de l' `Strings` élément, qui doit contenir un `String` élément dont les `Name` Propriétés et sont `Culture` définies de façon à correspondre aux `Name` `Culture` Propriétés et de `Package` . |
| `LicenseAgreement` | facultatif. Spécifie le nom du fichier dans le package de distribution qui contient le contrat de licence utilisateur final (CLUF).  Il peut s’agir d’un fichier de texte brut (*. txt*) ou d’un format de texte enrichi. (*. rtf*) |

## <a name="example"></a>Exemple
 L’exemple de code suivant montre un fichier de package complet pour redistribuer le .NET Framework 2,0.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Package
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  Name="DisplayName"
  Culture="Culture"
  LicenseAgreement="eula.rtf"
>

    <PackageFiles>
        <PackageFile Name="eula.rtf"/>
    </PackageFiles>

    <!-- Defines a localizable string table for error messages-->
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

</Package>
```

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)