---
title: Tâche GetOutputFileName | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 9733aae5e53948cdf07d62f62cd7ca5f930d08a3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747303"
---
# <a name="getoutputfilename-task"></a>Tâche GetOutputFileName

Tâche d’assistance visant à obtenir le nom du fichier de sortie pour cl et d’autres outils, qui permet de ne spécifier que le répertoire de sortie, le nom de fichier complet, ou rien du tout.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche **GetOutputFileName**.

|Paramètre|Description|
|---------------|-----------------|
|**OutputExtension**|Paramètre **String** obligatoire.|
|**OutputFile**|Paramètre de sortie de **chaîne** facultatif.|
|**OutputPath**|Paramètre de **chaîne** facultatif.|
|**SourceFile**|Paramètre **String** obligatoire.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)