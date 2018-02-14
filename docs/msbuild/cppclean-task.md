---
title: "CPPClean, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.cppclean
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), CPPClean task
- CPPClean task (MSBuild (Visual C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 37f976d54e3a18d3bc854b46678f79ecec41659f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="cppclean-task"></a>CPPClean, tâche
Supprime les fichiers temporaires créés par MSBuild quand un projet Visual C++ est généré. Le processus de suppression des fichiers de build est appelé *nettoyage*.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche **CPPClean**.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**DeletedFiles**|Paramètre de sortie `ITaskItem[]` facultatif.<br /><br /> Définit un tableau d’éléments de fichier de sortie MSBuild pouvant être consommés et émis par des tâches.|  
|**DoDelete**|Paramètre **booléen** facultatif.<br /><br /> Si `true`, nettoie les fichiers de build temporaires.|  
|**FilePatternsToDeleteOnClean**|Paramètre `String` requis.<br /><br /> Spécifie la liste des extensions de fichiers (séparées par des points-virgules) à nettoyer.|  
|**FilesExcludedFromClean**|Paramètre `String` facultatif.<br /><br /> Spécifie la liste des fichiers (séparés par des points-virgules) à ne pas nettoyer.|  
|**FoldersToClean**|Paramètre `String` requis.<br /><br /> Spécifie la liste des répertoires (séparés par des points-virgules) à nettoyer. Vous pouvez spécifier un chemin complet ou relatif contenant un caractère générique (**\***).|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)