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
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d66a7be3751e74ff75787ef194f90da1dcd1d3ce
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593289"
---
# <a name="getoutputfilename-task"></a>Tâche GetOutputFileName

Tâche d’assistance visant à obtenir le nom du fichier de sortie pour cl et d’autres outils, qui permet de ne spécifier que le répertoire de sortie, le nom de fichier complet, ou rien du tout.

## <a name="parameters"></a>Paramètres

Le tableau ci-dessous décrit les paramètres de la tâche **GetOutputFileName**.

|Paramètre|Description|
|---------------|-----------------|
|**OutputExtension**|Paramètre **de chaîne** requis.|
|**Outputfile**|Paramètre de sortie de **chaîne** facultatif.|
|**Outputpath**|Paramètre **de chaîne** facultatif.|
|**SourceFile (en)**|Paramètre **de chaîne** requis.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
