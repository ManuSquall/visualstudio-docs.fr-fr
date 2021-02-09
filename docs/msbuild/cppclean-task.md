---
title: CPPClean, tâche | Microsoft Docs
description: Cet article décrit la tâche CPPClean,, qui permet de supprimer les fichiers temporaires créés par MSBuild lors de la génération d’un projet C++.
ms.custom: SEO-VS-2020
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
- MSBuild (C++), CPPClean task
- CPPClean task (MSBuild (C++))
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a5b3d48c4556cfd05e5ce3f2b893b3f0e9a07226
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901438"
---
# <a name="cppclean-task"></a>CPPClean, tâche

Supprime les fichiers temporaires créés par MSBuild lors de la génération d’un projet C++. Le processus de suppression des fichiers de build est appelé *nettoyage*.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche **CPPClean**.

|Paramètre|Description|
|---------------|-----------------|
|**DeletedFiles**|Paramètre de sortie `ITaskItem[]` facultatif.<br /><br /> Définit un tableau d’éléments de fichier de sortie MSBuild pouvant être consommés et émis par des tâches.|
|**DoDelete**|Paramètre **booléen** facultatif.<br /><br /> Si `true`, nettoie les fichiers de build temporaires.|
|**FilePatternsToDeleteOnClean**|Paramètre `String` requis.<br /><br /> Spécifie la liste des extensions de fichiers (séparées par des points-virgules) à nettoyer.|
|**FilesExcludedFromClean**|Paramètre `String` facultatif.<br /><br /> Spécifie la liste des fichiers (séparés par des points-virgules) à ne pas nettoyer.|
|**FoldersToClean**|Paramètre `String` requis.<br /><br /> Spécifie la liste des répertoires (séparés par des points-virgules) à nettoyer. Vous pouvez spécifier un chemin d’accès complet ou relatif comportant le caractère générique (*).|

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
