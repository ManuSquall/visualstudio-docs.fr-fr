---
title: "GetReferenceAssemblyPaths Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# GetReferenceAssemblyPaths Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Retourne les chemins d'accès des assemblys de référence des différentes infrastructures.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `GetReferenceAssemblyPaths`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Paramètre de sortie `String[]` facultatif.<br /><br /> Renvoie le chemin d'accès, selon le paramètre `TargetFrameworkMoniker`.  Si `TargetFrameworkMoniker` est null ou vide, ce chemin d'accès est `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Paramètre de sortie `String[]` facultatif.<br /><br /> Renvoie le chemin d'accès, basé sur le paramètre `TargetFrameworkMoniker`, sans tenir compte de la partie profil du moniker.  Si `TargetFrameworkMoniker` est null ou vide, ce chemin d'accès est `String.Empty`.|  
|`TargetFrameworkMoniker`|Paramètre `String` facultatif.<br /><br /> Spécifie le moniker du Framework cible qui est associé aux chemins d'accès des assemblys de référence.|  
|`RootPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin d'accès racine à utiliser pour générer le chemin d'accès de l'assembly de référence.|  
|`BypassFrameworkInstallChecks`|Paramètre [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) facultatif.<br /><br /> Si la valeur est `true`, contourne les vérifications de base que `GetReferenceAssemblyPaths` effectue par défaut pour s'assurer que certaines versions du runtime .NET Framework sont installées en fonction du Framework cible.|  
|`TargetFrameworkMonikerDisplayName`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie le nom d'affichage du moniker du Framework cible.|  
  
## Notes  
 En plus des paramètres répertoriés dans le tableau, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle\-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)