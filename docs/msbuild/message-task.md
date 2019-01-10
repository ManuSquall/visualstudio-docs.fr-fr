---
title: Message, tâche | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 84f169d221ad8e6920844f2ccc2675277bb4af74
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869831"
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
 La tâche `Message` permet aux projets [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] d’envoyer des messages à des enregistreurs d’événements à différentes étapes du processus de génération.  
  
 Si le paramètre `Condition` a la valeur `true`, la valeur du paramètre `Text` est consignée dans le journal et la génération se poursuit. Si un paramètre `Condition` n’existe pas, le texte du message est consigné dans le journal. Pour plus d’informations sur la journalisation, voir [Obtenir des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Par défaut, le message est envoyé à l’enregistreur d’événements de la console MSBuild. Ceci peut être modifié en définissant le paramètre <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>. L’enregistreur d’événements interprète le paramètre `Importance`.  
  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).  
  
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
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)   
 [Obtenir des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)