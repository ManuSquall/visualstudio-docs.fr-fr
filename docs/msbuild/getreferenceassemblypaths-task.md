---
title: Tâche GetReferenceAssemblyPaths | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2ca532e37fa2f70800416539a7de2ff5e9978e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633978"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths, tâche

Retourne les chemins des assemblys de référence des différents frameworks.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `GetReferenceAssemblyPaths` .

|Paramètre|Description|
|---------------|-----------------|
|`ReferenceAssemblyPaths`|Paramètre de sortie `String[]` facultatif.<br /><br /> Retourne le chemin, en fonction du paramètre `TargetFrameworkMoniker`. Si `TargetFrameworkMoniker` est null ou vide, ce chemin est `String.Empty`.|
|`FullFrameworkReferenceAssemblyPaths`|Paramètre de sortie `String[]` facultatif.<br /><br /> Retourne le chemin, en fonction du paramètre `TargetFrameworkMoniker`, sans tenir compte de la partie profil du moniker. Si `TargetFrameworkMoniker` est null ou vide, ce chemin est `String.Empty`.|
|`TargetFrameworkMoniker`|Paramètre `String` facultatif.<br /><br /> Spécifie le moniker de la version cible de .NET Framework qui est associé aux chemins des assemblys de référence.|
|`RootPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin racine à utiliser pour générer le chemin de l’assembly de référence.|
|`BypassFrameworkInstallChecks`|Paramètre <xref:System.Boolean> facultatif.<br /><br /> Si la valeur est `true`, contourne les vérifications de base que `GetReferenceAssemblyPaths` effectue par défaut pour s’assurer que certaines versions du runtime .NET Framework sont installées en fonction de la version cible de .NET Framework.|
|`TargetFrameworkMonikerDisplayName`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie le nom d’affichage du moniker de la version cible de .NET Framework.|

## <a name="remarks"></a>Notes

 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)