---
title: Warning, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: adbddc2fb36e5036e535dfc1049945187fe14ed0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62558487"
---
# <a name="warning-task"></a>Warning, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Enregistre un avertissement durant une génération en fonction d’une instruction conditionnelle évaluée.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `Warning`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Code`|Paramètre `String` facultatif.<br /><br /> Code d’avertissement à associer à l’avertissement.|  
|`File`|Paramètre `String` facultatif.<br /><br /> Spécifie le fichier approprié, le cas échéant. Si aucun fichier n’est fourni, le fichier qui contient la tâche d’avertissement (Warning) est utilisé.|  
|`HelpKeyword`|Paramètre `String` facultatif.<br /><br /> Mot clé d’aide à associer à l’avertissement.|  
|`Text`|Paramètre `String` facultatif.<br /><br /> Texte d’avertissement que [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] journalise si le paramètre `Condition` a la valeur `true`.|  
  
## <a name="remarks"></a>Notes  
 La tâche `Warning` permet aux projets [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] de vérifier la présence d’une configuration requise ou d’une propriété obligatoire avant de passer à l’étape de génération suivante.  
  
 Si le paramètre `Condition` de la tâche `Warning` a la valeur `true`, la valeur du paramètre `Text` est journalisée et la génération se poursuit. Si aucun paramètre `Condition` n’existe, le texte de l’avertissement est journalisé. Pour plus d’informations sur la journalisation, consultez [obtention de journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension> , qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task> . Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant vérifie les propriétés définies sur la ligne de commande. Si aucune propriété n’est définie, le projet déclenche un événement d’avertissement et journalise la valeur du paramètre `Text` de la tâche `Warning`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Obtention des journaux de génération](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Référence de schéma de fichier de projet](../msbuild/msbuild-project-file-schema-reference.md)
