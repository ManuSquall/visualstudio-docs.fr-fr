---
title: VCMessage, tâche | Microsoft Docs
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (C++))
- MSBuild (C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be4f963a5944882f14118be54e498fd4712c2e46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747181"
---
# <a name="vcmessage-task"></a>VCMessage (tâche)
Journalise les messages d’avertissement et d’erreur lors de la génération.

## <a name="remarks"></a>Notes
 Cette tâche aide à implémenter C++ MSBuild pour les projets et n’est pas destinée à être appelée par l’utilisateur. Pour plus d'informations, consultez <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Paramètres
 Le tableau ci-dessous décrit les paramètres de la tâche **VCMessage**.

|Paramètre|Description|
|---------------|-----------------|
|**Arguments**|Paramètre **String** facultatif.<br /><br /> Liste de messages (séparés par des points-virgules) devant être affichée.|
|**Code**|Paramètre **String** obligatoire.<br /><br /> Numéro d’erreur qui qualifie le message.|
|**Type**|Paramètre **String** facultatif.<br /><br /> Spécifie le type de message à émettre. Spécifie soit « Warning » pour émettre un message d’avertissement, soit « Error » pour émettre un message d’erreur.|

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)