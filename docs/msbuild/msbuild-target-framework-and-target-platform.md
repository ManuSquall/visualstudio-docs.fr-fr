---
title: Framework cible et plateforme cible (MSBuild) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00874c8fd7ded67c380de1166d7e9753a3bd3c24
ms.sourcegitcommit: 044bb54cb4552c8f4651feb11d62e52726117e75
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68662049"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Version cible de .NET Framework et plateforme cible MSBuild
Un projet peut être généré pour s’exécuter sur un *framework cible*, qui est une version particulière du .NET Framework, et sur une *plateforme cible*, qui est une architecture logicielle particulière.  Par exemple, vous pouvez cibler une application pour qu’elle s’exécute sur le .NET Framework 2.0, sur une plateforme 32 bits compatible avec la famille de processeurs 802x86 (« x86 »). La combinaison de framework cible et de plateforme cible porte le nom de *contexte cible*.

> [!IMPORTANT]
> Cet article présente l’ancienne façon de spécifier un framework cible. Les projets de style SDK permettent l’utilisation de différents frameworks cibles, comme .NET Standard. Pour plus d’informations, consultez [Frameworks cibles](/dotnet/standard/frameworks).

## <a name="target-framework-and-profile"></a>Version cible de .NET Framework et profil cible
 Un framework cible est la version particulière du .NET Framework sur laquelle le projet généré doit s’exécuter. La spécification d'une version cible du .NET Framework est nécessaire, car elle active des fonctionnalités du compilateur et des références d'assemblys qui sont spécifiques à cette version du .NET Framework.

 Les versions du .NET Framework actuellement disponibles sont les suivantes :

- .NET Framework 2.0 (inclus dans Visual Studio 2005)

- .NET Framework 3.0 (inclus dans [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)])

- .NET Framework 3.5 (inclus dans [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)])

- .NET Framework 4.5.2

- .NET Framework 4.6 (inclus dans [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)])

- .NET Framework 4.6.1

- .NET Framework 4.6.2

- .NET Framework 4.7

- .NET Framework 4.7.1

- .NET Framework 4.7.2

- .NET Framework 4.8

Les versions du .NET Framework diffèrent l'une de l'autre quant à la liste d'assemblys que vous pouvez référencer. Par exemple, vous ne pouvez créer des applications Windows Presentation Foundation (WPF) que si votre projet cible le .NET Framework version 3.0 ou supérieure.

La version cible du .NET Framework est spécifiée dans la propriété `TargetFrameworkVersion` du fichier projet. Vous pouvez changer la version cible du .NET Framework pour un projet en utilisant les pages des propriétés du projet dans l'environnement de développement intégré (IDE) Visual Studio. Pour plus d'informations, voir [Procédure : cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Les valeurs disponibles pour `TargetFrameworkVersion` sont `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v4.6.1`, `v4.6.2`, `v4.7`, `v4.7.1`, `v4.7.2` et `v4.8`.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 Un *profil cible* est un sous-ensemble d’un framework cible. Par exemple, le profil Client .NET Framework 4 n'inclut pas de références aux assemblys MSBuild.

 Le profil cible est spécifié dans la propriété `TargetFrameworkProfile` d'un fichier projet. Vous pouvez changer le profil cible en utilisant le contrôle de la version cible du .NET Framework dans les pages des propriétés du projet dans l'IDE. Pour plus d'informations, voir [Procédure : cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>Plateforme cible
 Une *plateforme* est une combinaison de matériel et de logiciel qui définit un environnement d’exécution spécifique. Par exemple :

- `x86` désigne un système d'exploitation Windows 32 bits qui s'exécute sur un processeur Intel 80x86 ou son équivalent.

- `x64` désigne un système d’exploitation Windows 64 bits qui s’exécute sur un processeur Intel x64 ou son équivalent.

- `Xbox` désigne la plateforme Microsoft Xbox 360.

Une *plateforme cible* est la plateforme particulière sur laquelle votre projet généré doit s’exécuter. La plateforme cible est spécifiée dans la propriété de build `PlatformTarget` d'un fichier projet. Vous pouvez changer la plateforme cible en utilisant les pages de propriétés du projet ou le **Gestionnaire de configurations** dans l’IDE.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

Une *configuration cible* est un sous-ensemble d’une plateforme cible. Par exemple, la configuration `x86``Debug` n’inclut pas la plupart des optimisations du code. La configuration cible est spécifiée dans la propriété de build `Configuration` d'un fichier projet. Vous pouvez changer la configuration cible en utilisant les pages de propriétés du projet ou le **Gestionnaire de configurations**.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
<PropertyGroup>

```

## <a name="see-also"></a>Voir aussi
- [Multiciblage](../msbuild/msbuild-multitargeting-overview.md)
