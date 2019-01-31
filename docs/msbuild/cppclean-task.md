---
title: CPPClean, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: faf3650bdc190f498d981db5a0cd50867e86cdba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934876"
---
# <a name="cppclean-task"></a>CPPClean, tâche
Supprime les fichiers temporaires créés par MSBuild quand un projet Visual C++ est généré. Le processus de suppression des fichiers de build est appelé *nettoyage*.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche **CPPClean**.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**DeletedFiles**|Paramètre de sortie `ITaskItem[]` facultatif.<br /><br /> Définit un tableau d’éléments de fichier de sortie MSBuild pouvant être consommés et émis par des tâches.|  
|**DoDelete**|Paramètre **Boolean** facultatif.<br /><br /> Si `true`, nettoie les fichiers de build temporaires.|  
|**FilePatternsToDeleteOnClean**|Paramètre `String` requis.<br /><br /> Spécifie la liste des extensions de fichiers (séparées par des points-virgules) à nettoyer.|  
|**FilesExcludedFromClean**|Paramètre `String` facultatif.<br /><br /> Spécifie la liste des fichiers (séparés par des points-virgules) à ne pas nettoyer.|  
|**FoldersToClean**|Paramètre `String` requis.<br /><br /> Spécifie la liste des répertoires (séparés par des points-virgules) à nettoyer. Vous pouvez spécifier un chemin d’accès complet ou relatif comportant le caractère générique (*).|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)