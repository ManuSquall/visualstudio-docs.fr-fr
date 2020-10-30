---
title: SGen, tâche | Microsoft Docs
description: Découvrez comment MSBuild utilise la tâche SGen pour créer un assembly de sérialisation XML pour les types, en encapsulant l’outil XML Serializer Generator Sgen.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de2437306dba50a1f93b0b94d86af6351b17c0b6
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048350"
---
# <a name="sgen-task"></a>SGen (tâche)

Crée un assembly de sérialisation XML pour les types dans l’assembly spécifié. Cette tâche encapsule l’outil XML Serializer Generator ( *Sgen.exe* ). Pour plus d’informations, consultez [outil XML Serializer Generator (Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe).

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `SGen` .

| Paramètre | Description |
|-----------------------------| - |
| `BuildAssemblyName` | Paramètre `String` requis.<br /><br /> Assembly pour lequel le code de sérialisation doit être généré. |
| `BuildAssemblyPath` | Paramètre `String` requis.<br /><br /> Chemin de l’assembly pour lequel le code de sérialisation doit être généré. |
| `DelaySign` | Paramètre `Boolean` facultatif.<br /><br /> Si `true`, indique que vous souhaitez placer uniquement la clé publique dans l’assembly. Si `false`, indique que vous souhaitez obtenir un assembly complètement signé.<br /><br /> Ce paramètre n’a aucun effet, sauf s’il est utilisé avec les paramètres `KeyFile` ou `KeyContainer`. |
| `KeyContainer` | Paramètre `String` facultatif.<br /><br /> Spécifie un conteneur qui contient une paire de clés. Cela signe l’assembly en insérant une clé publique dans le manifeste d’assembly. La tâche signe ensuite l’assembly définitif à l’aide de la clé privée. |
| `KeyFile` | Paramètre `String` facultatif.<br /><br /> Spécifie une paire de clés ou une clé publique pour signer un assembly. Le compilateur insère la clé publique dans le manifeste d'assembly, puis signe l'assembly final avec la clé privée. |
| `Platform` | Paramètre `String` facultatif.<br /><br /> Obtient ou définit la plateforme du compilateur utilisée pour générer l’assembly de sortie. Ce paramètre peut avoir la valeur `x86`, `x64` ou `anycpu`. La valeur par défaut est `anycpu`. |
| `References` | Paramètre `String[]` facultatif.<br /><br /> Spécifie les assemblys référencés par les types qui requièrent la sérialisation XML. |
| `SdkToolsPath` | Paramètre `String` facultatif.<br /><br /> Spécifie le chemin d’accès aux outils du kit de développement logiciel (SDK), par exemple *resgen.exe* . |
| `SerializationAssembly` | Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient l’assembly de sérialisation généré. |
| `SerializationAssemblyName` | Paramètre `String` facultatif.<br /><br /> Spécifie le nom de l’assembly de sérialisation généré. |
| `ShouldGenerateSerializer` | Paramètre `Boolean` requis.<br /><br /> Si `true`, la tâche SGen doit générer un assembly de sérialisation. |
| `Timeout` | Paramètre `Int32` facultatif.<br /><br /> Spécifie le délai, en millisecondes, après lequel l’exécutable de la tâche est arrêté. La valeur par défaut est `Int.MaxValue`, ce qui indique qu’il n’existe aucun délai d’expiration. |
| `ToolPath` | Paramètre `String` facultatif.<br /><br /> Spécifie l’emplacement à partir duquel la tâche chargera le fichier exécutable sous-jacent ( *sgen.exe* ). Si ce paramètre n’est pas spécifié, la tâche utilise le chemin d’installation du kit de développement logiciel (SDK) correspondant à la version du Framework qui exécute MSBuild. |
| `Types` | Paramètre `String[]` facultatif.<br /><br /> Obtient ou définit une liste de types spécifiques pour lesquels générer le code de sérialisation. SGen générera le code de sérialisation uniquement pour ces types. |
| `UseProxyTypes` | Paramètre `Boolean` requis.<br /><br /> Si `true`, la tâche SGen génère du code de sérialisation uniquement pour les types de proxy de service web XML. |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Tâches](../msbuild/msbuild-tasks.md)
- [Concepts MSBuild](../msbuild/msbuild-concepts.md)
