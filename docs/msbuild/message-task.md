---
title: Message, tâche | Microsoft Docs
description: En savoir plus sur les paramètres et les paramètres de la tâche de message MSBuild, qui journalise les messages pendant les builds.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b7a2854220a7ee85fd680cedd8c8e0c5c3ada89
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903841"
---
# <a name="message-task"></a>Message (tâche)

Enregistre un message pendant une génération.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `Message` .

|Paramètre|Description|
|---------------|-----------------|
|`Importance`|Paramètre `String` facultatif.<br /><br /> Spécifie l’importance du message. Ce paramètre peut avoir la valeur `high`, `normal` ou `low`. La valeur par défaut est `normal`.|
|`Text`|Paramètre `String` facultatif.<br /><br /> Texte d’erreur à consigner.|

## <a name="remarks"></a>Notes

 La `Message` tâche permet aux projets MSBuild d’émettre des messages aux enregistreurs d’événements à différentes étapes du processus de génération.

 Si le paramètre `Condition` a la valeur `true`, la valeur du paramètre `Text` est consignée dans le journal et la génération se poursuit. Si un paramètre `Condition` n’existe pas, le texte du message est consigné dans le journal. Pour plus d’informations sur la journalisation, voir [Obtenir des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md).

 Par défaut, le message est envoyé à tous les enregistreurs d’événements inscrits. L’enregistreur d’événements interprète le paramètre `Importance`. En règle générale, un message dont la valeur `high` est est envoyé lorsque le niveau de détail de l’enregistreur est défini sur <xref:Microsoft.Build.Framework.LoggerVerbosity> .`Minimal` ou ultérieure. Un message dont la valeur `low` est est envoyé lorsque le niveau de détail de l’enregistreur est défini sur <xref:Microsoft.Build.Framework.LoggerVerbosity> . `Detailed`

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemple

 L’exemple de code suivant consigne les messages dans tous les enregistreurs d’événements inscrits.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="DisplayMessages">
        <Message Text="Project File Name = $(MSBuildProjectFile)" />
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Obtenir des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)
