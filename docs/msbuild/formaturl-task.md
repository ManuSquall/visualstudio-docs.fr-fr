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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9a05ce16289c012b067faa5bc302a3921cbe1c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888093"
---
# <a name="formaturl-task"></a>FormatUrl (tâche)

Convertit une URL en URL au format correct.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `FormatUrl` .

|Paramètre|Description|
|---------------|-----------------|
|`InputUrl`|Paramètre `String` facultatif.<br /><br /> Spécifie l’URL à mettre en forme.|
|`OutputUrl`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie l’URL mise en forme.|

## <a name="remarks"></a>Notes

 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Voir aussi

- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)