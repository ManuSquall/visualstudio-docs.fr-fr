---
title: "ResolveKeySource Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ResolveKeySource task [MSBuild]"
  - "MSBuild, ResolveKeySource task"
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# ResolveKeySource Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Détermine la source des clés avec nom fort.  
  
## Paramètres de la tâche  
 Le tableau suivant décrit les paramètres de la tâche `ResolveKeySource`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|Paramètre `Int32` facultatif.<br /><br /> Obtient ou définit la durée, en secondes, pour afficher le message de compte à rebours.|  
|`AutoClosePasswordPromptTimeout`|Paramètre `Int32` facultatif.<br /><br /> Obtient ou définit la durée, en secondes, d'attente avant de fermer la boîte de dialogue d'invite de saisie du mot de passe.|  
|`CertificateFile`|Paramètre `String` facultatif.<br /><br /> Obtient ou définit le chemin d'accès du fichier de certificat.|  
|`CertificateThumbprint`|Paramètre `String` facultatif.<br /><br /> Obtient ou définit l'empreinte numérique du certificat.|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Obtient ou définit le chemin d'accès du fichier de clé.|  
|`ResolvedKeyContainer`|Paramètre de sortie `String` facultatif.<br /><br /> Obtient ou définit le conteneur de clé résolu.|  
|`ResolvedKeyFile`|Paramètre de sortie `String` facultatif.<br /><br /> Obtient ou définit le fichier de clé résolu.|  
|`ResolvedThumbprint`|Paramètre de sortie `String` facultatif.<br /><br /> Obtient ou définit l'empreinte numérique résolue du certificat.|  
|`ShowImportDialogDespitePreviousFailures`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, afficher la boîte de dialogue d'importation malgré les échecs précédents.|  
|`SuppressAutoClosePasswordPrompt`|Paramètre `Boolean` facultatif.<br /><br /> Obtient ou définit une valeur booléenne qui indique si la boîte de dialogue d'invite de saisie du mot de passe ne doit pas se fermer automatiquement.|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)