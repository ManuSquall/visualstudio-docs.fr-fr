---
title: GetFrameworkSdkPath, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16a522044188db854b89f87ccba0ef3393ab70fc
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54803934"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Récupère le chemin au [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `GetFrameworkSdkPath`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Paramètre de sortie en lecture seule `String` facultatif.<br /><br /> Retourne le chemin du SDK .NET version 2.0, s’il est présent. Sinon, retourne `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Paramètre de sortie en lecture seule `String` facultatif.<br /><br /> Retourne le chemin du SDK .NET version 3.5, s’il est présent. Sinon, retourne `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Paramètre de sortie en lecture seule `String` facultatif.<br /><br /> Retourne le chemin du SDK .NET version 4.0, s’il est présent. Sinon, retourne `String.Empty`.|  
|`Path`|Paramètre de sortie `String` facultatif.<br /><br /> Contient le chemin de la dernière version du SDK .NET, si une version est présente. Sinon, retourne `String.Empty`.|  
  
## <a name="remarks"></a>Remarques  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche `GetFrameworkSdkPath` pour stocker le chemin du [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] dans la propriété `SdkPath`.  
  
```  
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
