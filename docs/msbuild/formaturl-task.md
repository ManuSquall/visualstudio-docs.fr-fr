---
title: FormatUrl, tâche | Microsoft Docs
description: Découvrez comment utiliser la tâche MSBuild FormatUrl pour convertir une URL d’entrée dans un format d’URL de sortie correct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e38a0f1aea6999e30d2ab2493873f66cd907878
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436895"
---
# <a name="formaturl-task"></a>FormatUrl (tâche)

Convertit une URL en URL au format correct.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `FormatUrl` .

|Paramètre|Description|
|---------------|-----------------|
|`InputUrl`|Paramètre `String` facultatif.<br /><br /> Spécifie l’URL à mettre en forme.|
|`OutputUrl`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie l’URL mise en forme.|

## <a name="remarks"></a>Remarques

 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)