---
title: Vue d’ensemble du multiciblage MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 609c764192673e4d3f9fbd99a1bc572e9d78db7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84183520"
---
# <a name="msbuild-multitargeting-overview"></a>Vue d’ensemble du multiciblage MSBuild

MSBuild vous permet de compiler une application pour l’exécuter sur une version du .NET Framework donnée et sur une plateforme système donnée. Par exemple, vous pouvez compiler une application qui s’exécute sur le .NET Framework version 2.0 sur une plateforme 32 bits, et compiler la même application pour qu’elle s’exécute sur le .NET Framework version 4.5 sur une plateforme 64 bits.

> [!IMPORTANT]
> Malgré le nom « multiciblage », un projet peut cibler uniquement un seul framework et une seule plateforme à la fois.

 Voici quelques-unes des fonctionnalités de ciblage de MSBuild :

- Vous pouvez développer une application qui cible une version antérieure du .NET Framework (par exemple, la version 2.0, 3.5 ou 4).

- Vous pouvez cibler des Frameworks autre que le .NET Framework (par exemple, Silverlight Framework).

- Vous pouvez cibler un *profil Framework*, qui est un sous-ensemble prédéfini d’une version cible de .NET Framework.

- Si un service pack pour la version actuelle du .NET Framework est publié, vous pouvez le cibler.

- Le ciblage MSBuild garantit qu’une application utilise uniquement les fonctionnalités qui sont disponibles dans le Framework et la plateforme ciblés.

## <a name="target-framework-and-platform"></a>Version cible de .NET Framework et plateforme cible

 Un *Framework cible* correspond à la version du .NET Framework sur laquelle le projet s’exécute, et une *plateforme cible* à la plateforme système sur laquelle le projet s’exécute.  Par exemple, vous souhaiterez peut-être cibler une application .NET Framework 2,0 pour qu’elle s’exécute sur une plateforme 32 bits compatible avec la famille de processeurs 80x86 (x86). La combinaison de framework cible et de plateforme cible porte le nom de *contexte cible*. Pour plus d’informations, consultez [Version cible de .NET Framework et plateforme cible](../msbuild/msbuild-target-framework-and-target-platform.md).

## <a name="toolset-toolsversion"></a>Ensemble d'outils (ToolsVersion)

 Un ensemble d’outils regroupe les outils, tâches et cibles utilisés pour créer l’application. Un ensemble d’outils comprend des compilateurs tels que *csc.exe* et *vbc.exe*, le fichier de cibles communes (*Microsoft. Common. targets*) et le fichier de tâches courantes (*Microsoft. Common. Tasks*). L’ensemble d’outils 4.5 peut être utilisé pour cibler des versions 2.0, 3.0, 3.5, 4 et 4.5 du .NET Framework. Cependant, l’ensemble d’outils 2.0 ne peut être utilisé que pour cibler le .NET Framework version 2.0. Pour plus d’informations, consultez [Ensemble d’outils (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).

## <a name="reference-assemblies"></a>Assemblys de référence

 Les assemblys de référence qui sont spécifiés dans l’ensemble d’outils vous aident à concevoir et à générer une application. Ces assemblys de référence activent non seulement une build cible particulière, mais limitent également les composants et fonctionnalités dans l’IDE Visual Studio à ceux qui sont compatibles avec la cible. Pour plus d’informations, voir [Résoudre des assemblys au moment du design](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="configure-targets-and-tasks"></a>Configurer les cibles et les tâches

 Vous pouvez configurer des cibles et des tâches MSBuild pour qu’elles s’exécutent hors processus avec MSBuild. Vous pouvez ainsi cibler des contextes très différents de celui dans lequel vous vous trouvez.  Par exemple, vous pouvez cibler une application .NET Framework 2.0 32 bits alors que l’ordinateur de développement s’exécute sur une plateforme 64 bits avec le .NET Framework 4.5. Pour plus d’informations, voir [Configurer des cibles et des tâches](../msbuild/configuring-targets-and-tasks.md).

## <a name="troubleshooting"></a>Dépannage

 Des erreurs peuvent se produire si vous tentez de référencer un assembly qui ne fait pas partie du contexte cible. Pour plus d’informations sur ces erreurs et la procédure à suivre pour y remédier, consultez [Résoudre les problèmes liés aux erreurs de ciblage du .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).
