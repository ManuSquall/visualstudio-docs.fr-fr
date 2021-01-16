---
title: Framework cible et plateforme cible (MSBuild) | Microsoft Docs
description: Découvrez comment générer un projet MSBuild pour qu’il s’exécute sur une version cible de .NET Framework, ainsi qu’une plateforme ou une architecture logicielle cible.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 958f33a39126f8f48cf29bad1c25c7d962513ed0
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533860"
---
# <a name="msbuild-target-framework-and-target-platform"></a>Version cible de .NET Framework et plateforme cible MSBuild

Un projet peut être généré pour s’exécuter sur un *framework cible*, qui est une version particulière du .NET Framework, et sur une *plateforme cible*, qui est une architecture logicielle particulière.  Par exemple, vous pouvez cibler une application pour qu’elle s’exécute sur le .NET Framework 2,0 sur une plateforme 32 bits qui est compatible avec la famille de processeurs 80x86 (« x86 »). La combinaison de framework cible et de plateforme cible porte le nom de *contexte cible*.

> [!IMPORTANT]
> Cet article présente l’ancienne façon de spécifier un framework cible. Les projets de style SDK permettent l’utilisation de différents frameworks cibles, comme .NET Standard. Pour plus d’informations, consultez [Frameworks cibles](/dotnet/standard/frameworks).

## <a name="target-framework-and-profile"></a>Version cible de .NET Framework et profil cible

 Un framework cible est la version particulière du .NET Framework sur laquelle le projet généré doit s’exécuter. La spécification d'une version cible du .NET Framework est nécessaire, car elle active des fonctionnalités du compilateur et des références d'assemblys qui sont spécifiques à cette version du .NET Framework.

 Les versions du .NET Framework actuellement disponibles sont les suivantes :

- .NET Framework 2.0 (inclus dans Visual Studio 2005)

- Le .NET Framework 3,0 (inclus dans Windows Vista)

- .NET Framework 3,5 (inclus dans Visual Studio 2008)

- .NET Framework 4.5.2

- .NET Framework 4,6 (inclus dans Visual Studio 2015)

- .NET Framework 4.6.1

- .NET Framework 4.6.2

- .NET Framework 4.7

- .NET Framework 4.7.1

- .NET Framework 4.7.2

- .NET Framework 4.8

Les versions du .NET Framework diffèrent l'une de l'autre quant à la liste d'assemblys que vous pouvez référencer. Par exemple, vous ne pouvez créer des applications Windows Presentation Foundation (WPF) que si votre projet cible le .NET Framework version 3.0 ou supérieure.

La version cible du .NET Framework est spécifiée dans la propriété `TargetFrameworkVersion` du fichier projet. Vous pouvez changer la version cible du .NET Framework pour un projet en utilisant les pages des propriétés du projet dans l'environnement de développement intégré (IDE) Visual Studio. Pour plus d’informations, consultez [Guide pratique pour cibler une version du .NET Framework](../ide/visual-studio-multi-targeting-overview.md). Les valeurs disponibles pour `TargetFrameworkVersion` sont `v2.0`, `v3.0`, `v3.5`, `v4.5.2`, `v4.6`, `v4.6.1`, `v4.6.2`, `v4.7`, `v4.7.1`, `v4.7.2` et `v4.8`.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 Un *profil cible* est un sous-ensemble d’un framework cible. Par exemple, le profil Client .NET Framework 4 n'inclut pas de références aux assemblys MSBuild.

 > [!NOTE]
 > Les profils cibles s’appliquent uniquement aux [bibliothèques de classes portables](/dotnet/standard/cross-platform/cross-platform-development-with-the-portable-class-library).

 Le profil cible est spécifié dans la propriété `TargetFrameworkProfile` d'un fichier projet. Vous pouvez changer le profil cible en utilisant le contrôle de la version cible du .NET Framework dans les pages des propriétés du projet dans l'IDE.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>Plateforme cible

 Une *plateforme* est une combinaison de matériel et de logiciel qui définit un environnement d’exécution spécifique. Par exemple,

- `x86` désigne un système d'exploitation Windows 32 bits qui s'exécute sur un processeur Intel 80x86 ou son équivalent.

- `x64` désigne un système d’exploitation Windows 64 bits qui s’exécute sur un processeur Intel x64 ou son équivalent.

- `Xbox` désigne la plateforme Microsoft Xbox 360.

Une *plateforme cible* est la plateforme particulière sur laquelle votre projet généré doit s’exécuter. La plateforme cible est spécifiée dans la propriété de build `PlatformTarget` d'un fichier projet. Vous pouvez changer la plateforme cible en utilisant les pages de propriétés du projet ou le **Gestionnaire de configurations** dans l’IDE.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

Une *configuration cible* est un sous-ensemble d’une plateforme cible. Par exemple, la configuration `x86` `Debug` n’inclut pas la plupart des optimisations du code. La configuration cible est spécifiée dans la propriété de build `Configuration` d'un fichier projet. Vous pouvez changer la configuration cible en utilisant les pages de propriétés du projet ou le **Gestionnaire de configurations**.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
</PropertyGroup>

```

## <a name="see-also"></a>Voir aussi

- [Multi-ciblage](../msbuild/msbuild-multitargeting-overview.md)
