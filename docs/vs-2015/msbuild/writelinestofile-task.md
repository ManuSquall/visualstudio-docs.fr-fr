---
title: WriteLinesToFile, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b25318a9b453ee9f9b05b22e7130555b5a14d556
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54760139"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Écrit les chemins des éléments spécifiés dans le fichier texte spécifié.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `WriteLinestoFile`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`File`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie le fichier où écrire les éléments.|  
|`Lines`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les éléments à écrire dans le fichier.|  
|`Overwrite`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, remplace le contenu existant dans le fichier.|  
|`Encoding`|Paramètre `String` facultatif.<br /><br /> Sélectionne l’encodage des caractères, par exemple « Unicode ».  Voir aussi <xref:System.Text.Encoding>.|  
  
## <a name="remarks"></a>Remarques  
 Si `Overwrite` est `true`, crée un fichier, écrit le contenu dans ce fichier, puis le ferme. Si le fichier cible existe déjà, il est remplacé. Si `Overwrite` est `false`, ajoute le contenu au fichier, en créant le fichier cible s’il n’existe pas.  
  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche `WriteLinesToFile` pour écrire les chemins des éléments de la collection d’éléments `MyItems` dans le fichier spécifié par la collection d’éléments `MyTextFile`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
