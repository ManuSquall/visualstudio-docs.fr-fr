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
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d025fd1f71b67acbcd532232b36b55fd35e1f530
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596059"
---
# <a name="vcmessage-task"></a>VCMessage (tâche)
Journalise les messages d’avertissement et d’erreur lors de la génération.

## <a name="remarks"></a>Remarques
 Cette tâche permet d’implémenter MSBuild pour Visual C++ et n’est pas destinée à être appelée par l’utilisateur. Pour plus d'informations, consultez <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Paramètres
 Le tableau ci-dessous décrit les paramètres de la tâche **VCMessage**.

|Paramètre|Description|
|---------------|-----------------|
|**Arguments**|Paramètre **String** facultatif.<br /><br /> Liste de messages (séparés par des points-virgules) devant être affichée.|
|**Code**|Paramètre **String** obligatoire.<br /><br /> Numéro d’erreur qui qualifie le message.|
|**Type**|Paramètre **String** facultatif.<br /><br /> Spécifie le type de message à émettre. Spécifie soit « Warning » pour émettre un message d’avertissement, soit « Error » pour émettre un message d’erreur.|

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)