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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67cdd6fa3517402dbd9c1e85a84f762f9aa7dd17
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816881"
---
# <a name="formatversion-task"></a>FormatVersion, tâche
Ajoute le numéro de révision au numéro de version.

- Cas n°1 : Entrée : Version=\<undefined>;  Revision=\<Peu importe>;   Output: OutputVersion="1.0.0.0"

- Cas n°2 : Entrée : Version="1.0.0.*"  Revision="5"  Output: OutputVersion="1.0.0.5"

- Cas n°3 : Entrée : Version="1.0.0.0"  Revision=\<Peu importe>;  Output: OutputVersion="1.0.0.0"

## <a name="parameters"></a>Paramètres
 Le tableau ci-dessous décrit les paramètres de la tâche `FormatVersion` .

|Paramètre|Description|
|---------------|-----------------|
|`FormatType`|Paramètre `String` facultatif.<br /><br /> Spécifie le type de format.<br /><br /> -   "Version" = version.<br />-   "Path" = remplacez "." par "_";|
|`OutputVersion`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie la version de la sortie qui inclut le numéro de révision.|
|`Revision`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la révision à ajouter à la version.|
|`Version`|Paramètre `String` facultatif.<br /><br /> Spécifie la chaîne de numéro de version à mettre en forme.|

## <a name="remarks"></a>Remarques
 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Voir aussi
- [Tâches](../msbuild/msbuild-tasks.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)