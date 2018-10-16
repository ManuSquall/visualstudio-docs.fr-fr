---
title: Tâche GetReferenceAssemblyPaths | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b885443fba9b92e1d4004987988e4d743f3921d1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244478"
---
# <a name="getreferenceassemblypaths-task"></a>Tâche GetReferenceAssemblyPaths
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Retourne les chemins des assemblys de référence des différents frameworks.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `GetReferenceAssemblyPaths` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Paramètre de sortie `String[]` facultatif.<br /><br /> Retourne le chemin, en fonction du paramètre `TargetFrameworkMoniker`. Si `TargetFrameworkMoniker` est null ou vide, ce chemin est `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Paramètre de sortie `String[]` facultatif.<br /><br /> Retourne le chemin, en fonction du paramètre `TargetFrameworkMoniker`, sans tenir compte de la partie profil du moniker. Si `TargetFrameworkMoniker` est null ou vide, ce chemin est `String.Empty`.|  
|`TargetFrameworkMoniker`|Paramètre `String` facultatif.<br /><br /> Spécifie le moniker de la version cible de .NET Framework qui est associé aux chemins des assemblys de référence.|  
|`RootPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin racine à utiliser pour générer le chemin de l’assembly de référence.|  
|`BypassFrameworkInstallChecks`|Facultatif [booléen] (<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) paramètre.<br /><br /> Si la valeur est `true`, contourne les vérifications de base que `GetReferenceAssemblyPaths` effectue par défaut pour s’assurer que certaines versions du runtime .NET Framework sont installées en fonction de la version cible de .NET Framework.|  
|`TargetFrameworkMonikerDisplayName`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie le nom d’affichage du moniker de la version cible de .NET Framework.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)



