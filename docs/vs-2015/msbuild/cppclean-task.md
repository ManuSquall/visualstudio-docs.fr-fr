---
title: CPPClean, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bddba1170cf675b5bde7ab8deed8cce1e7eb57dd
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654995"
---
# <a name="cppclean-task"></a>CPPClean, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Supprime les fichiers temporaires créés par MSBuild quand un projet Visual C++ est généré. Le processus de suppression des fichiers de build est appelé *nettoyage*.  

## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche **CPPClean**.  

|            Paramètre            |                                                                                                Description                                                                                                 |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        **DeletedFiles**         |                               Paramètre de sortie `ITaskItem[]` facultatif.<br /><br /> Définit un tableau d’éléments de fichier de sortie MSBuild pouvant être consommés et émis par des tâches.                                |
|          **DoDelete**           |                                                            Paramètre **Boolean** facultatif.<br /><br /> Si `true`, nettoie les fichiers de build temporaires.                                                             |
| **FilePatternsToDeleteOnClean** |                                            Paramètre `String` requis.<br /><br /> Spécifie la liste des extensions de fichiers (séparées par des points-virgules) à nettoyer.                                             |
|   **FilesExcludedFromClean**    |                                                    Paramètre `String` facultatif.<br /><br /> Spécifie la liste des fichiers (séparés par des points-virgules) à ne pas nettoyer.                                                    |
|       **FoldersToClean**        | Paramètre `String` requis.<br /><br /> Spécifie la liste des répertoires (séparés par des points-virgules) à nettoyer. Vous pouvez spécifier un chemin complet ou relatif comportant le caractère générique (**\\**\*). |

## <a name="remarks"></a>Notes  

## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
