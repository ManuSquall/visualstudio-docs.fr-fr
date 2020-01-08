---
title: FormatVersion, tâche | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b36c4eb63c503132aaf434c64249e4a5fdd3872
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595252"
---
# <a name="formatversion-task"></a>FormatVersion, tâche
Ajoute le numéro de révision au numéro de version.

- Cas #1 : Input: Version=\<undefined>;  Revision=\<peu importe>;   Output: OutputVersion="1.0.0.0"

- Cas #2 : Input: Version="1.0.0.*"  Revision="5"  Output: OutputVersion="1.0.0.5"

- Cas #3 : Input: Version="1.0.0.0"  Revision=\<peu importe>;  Output: OutputVersion="1.0.0.0"

## <a name="parameters"></a>Parameters
 Le tableau ci-dessous décrit les paramètres de la tâche `FormatVersion` .

|Paramètre|Description|
|---------------|-----------------|
|`FormatType`|Paramètre `String` facultatif.<br /><br /> Spécifie le type de format.<br /><br /> -   "Version" = version.<br />-   "Path" = remplacez "." par "_";|
|`OutputVersion`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie la version de la sortie qui inclut le numéro de révision.|
|`Revision`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la révision à ajouter à la version.|
|`Version`|Paramètre `String` facultatif.<br /><br /> Spécifie la chaîne de numéro de version à mettre en forme.|

## <a name="remarks"></a>Notes
 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Voir aussi
- [Tâches MSBuild](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
