---
title: "Message, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
caps.latest.revision: "23"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 2b2b66091c84606739b96f3aeca0b99fbaa2e950
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="message-task"></a>Message, tâche
Enregistre un message pendant une génération.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `Message`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Importance`|Paramètre `String` facultatif.<br /><br /> Spécifie l’importance du message. Ce paramètre peut avoir la valeur `high`, `normal` ou `low`. La valeur par défaut est `normal`.|  
|`Text`|Paramètre `String` facultatif.<br /><br /> Texte d’erreur à consigner.|  
  
## <a name="remarks"></a>Remarques  
 La tâche `Message` permet aux projets [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] d’envoyer des messages à des enregistreurs d’événements à différentes étapes du processus de génération.  
  
 Si le paramètre `Condition` a la valeur `true`, la valeur du paramètre `Text` est consignée dans le journal et la génération se poursuit. Si un paramètre `Condition` n’existe pas, le texte du message est consigné dans le journal. Pour plus d’informations sur la journalisation, consultez l’article [Obtention de journaux de génération avec MSBuild](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Par défaut, le message est envoyé à l’enregistreur d’événements de la console MSBuild. Ceci peut être modifié en définissant le paramètre <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>. L’enregistreur d’événements interprète le paramètre `Importance`.  
  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
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
 [Référence des tâches](../msbuild/msbuild-task-reference.md)   
 [Obtention de journaux de génération avec MSBuild](../msbuild/obtaining-build-logs-with-msbuild.md)