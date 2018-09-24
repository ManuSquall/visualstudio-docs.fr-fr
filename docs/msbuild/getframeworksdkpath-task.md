---
title: GetFrameworkSdkPath, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a3ce43a9b2acae5589e4b746ce4bf2b2a47b0111
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37946831"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath (tâche)
Récupère le chemin au [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `GetFrameworkSdkPath` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Paramètre de sortie en lecture seule `String` facultatif.<br /><br /> Retourne le chemin du SDK .NET version 2.0, s’il est présent. Sinon, retourne `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Paramètre de sortie en lecture seule `String` facultatif.<br /><br /> Retourne le chemin du SDK .NET version 3.5, s’il est présent. Sinon, retourne `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Paramètre de sortie en lecture seule `String` facultatif.<br /><br /> Retourne le chemin du SDK .NET version 4.0, s’il est présent. Sinon, retourne `String.Empty`.|  
|`Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin de la dernière version du SDK .NET, si une version est présente. Sinon, retourne `String.Empty`.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche `GetFrameworkSdkPath` pour stocker le chemin du [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] dans la propriété `SdkPath`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)