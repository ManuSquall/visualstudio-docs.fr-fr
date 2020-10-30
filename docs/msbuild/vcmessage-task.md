---
title: VCMessage, tâche | Microsoft Docs
description: Découvrez comment MSBuild utilise la tâche VCMessage, pour consigner les messages d’avertissement et d’erreur pendant une génération pour les projets C++.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8c01c86a5374c14ac27de1535020c5deed29a89f
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046752"
---
# <a name="vcmessage-task"></a>VCMessage (tâche)

Journalise les messages d’avertissement et d’erreur lors de la génération.

## <a name="remarks"></a>Remarques

 Cette tâche aide à implémenter MSBuild pour les projets C++ et n’est pas destinée à être appelée par l’utilisateur. Pour plus d'informations, consultez <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche **VCMessage** .

|Paramètre|Description|
|---------------|-----------------|
|**Arguments**|Paramètre de **chaîne** facultatif.<br /><br /> Liste de messages (séparés par des points-virgules) devant être affichée.|
|**Code**|Paramètre de **chaîne** obligatoire.<br /><br /> Numéro d’erreur qui qualifie le message.|
|**Type**|Paramètre de **chaîne** facultatif.<br /><br /> Spécifie le type de message à émettre. Spécifie soit « Warning » pour émettre un message d’avertissement, soit « Error » pour émettre un message d’erreur.|

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
