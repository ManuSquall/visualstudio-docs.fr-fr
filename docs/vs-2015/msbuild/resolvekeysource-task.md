---
title: ResolveKeySource, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49ba6bb58c8c3386da71da71b84b0cf07fc5ad23
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794069"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Détermine la source des clés à nom fort.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `ResolveKeySource`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|Paramètre `Int32` facultatif.<br /><br /> Obtient ou définit la durée d’affichage, en secondes, du message de compte à rebours.|  
|`AutoClosePasswordPromptTimeout`|Paramètre `Int32` facultatif.<br /><br /> Obtient ou définit le délai d’attente, en secondes, avant la fermeture de la boîte de dialogue d’invite de mot de passe.|  
|`CertificateFile`|Paramètre `String` facultatif.<br /><br /> Obtient ou définit le chemin du fichier de certificat.|  
|`CertificateThumbprint`|Paramètre `String` facultatif.<br /><br /> Obtient ou définit l’empreinte de certificat.|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Obtient ou définit le chemin du fichier de clé.|  
|`ResolvedKeyContainer`|Paramètre de sortie `String` facultatif.<br /><br /> Obtient ou définit le conteneur de clé résolu.|  
|`ResolvedKeyFile`|Paramètre de sortie `String` facultatif.<br /><br /> Obtient ou définit le fichier de clé résolu.|  
|`ResolvedThumbprint`|Paramètre de sortie `String` facultatif.<br /><br /> Obtient ou définit l’empreinte de certificat résolue.|  
|`ShowImportDialogDespitePreviousFailures`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, affiche la boîte de dialogue d’importation, malgré les échecs précédents.|  
|`SuppressAutoClosePasswordPrompt`|Paramètre `Boolean` facultatif.<br /><br /> Obtient ou définit une valeur booléenne qui spécifie si la boîte de dialogue d’invite de mot de passe ne doit pas se fermer automatiquement.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
