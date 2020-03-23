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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2247240ae0992c8275520ec5d7bf94d98ae1053
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631209"
---
# <a name="vcmessage-task"></a>VCMessage (tâche)

Journalise les messages d’avertissement et d’erreur lors de la génération.

## <a name="remarks"></a>Notes 

 Cette tâche permet de mettre en œuvre MSBuild pour les projets C et n’est pas destiné à être appelé par l’utilisateur. Pour plus d’informations, consultez <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche **VCMessage**.

|Paramètre|Description|
|---------------|-----------------|
|**Arguments**|Paramètre **de chaîne** facultatif.<br /><br /> Liste de messages (séparés par des points-virgules) devant être affichée.|
|**Code**|Paramètre **de chaîne** requis.<br /><br /> Numéro d’erreur qui qualifie le message.|
|**Type**|Paramètre **de chaîne** facultatif.<br /><br /> Spécifie le type de message à émettre. Spécifie soit « Warning » pour émettre un message d’avertissement, soit « Error » pour émettre un message d’erreur.|

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
