---
title: "GetFrameworkSdkPath, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 390df225104b8469e82d605c24e54e1025c60f37
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath, tâche
Récupère le chemin au [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `GetFrameworkSdkPath`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Paramètre de sortie en lecture seule `String` facultatif.<br /><br /> Retourne le chemin du SDK .NET version 2.0, s’il est présent. Sinon, retourne `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Paramètre de sortie en lecture seule `String` facultatif.<br /><br /> Retourne le chemin du SDK .NET version 3.5, s’il est présent. Sinon, retourne `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Paramètre de sortie en lecture seule `String` facultatif.<br /><br /> Retourne le chemin du SDK .NET version 4.0, s’il est présent. Sinon, retourne `String.Empty`.|  
|`Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin de la dernière version du SDK .NET, si une version est présente. Sinon, retourne `String.Empty`.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
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
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)