---
title: "CreateProperty, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: "11"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: a585c0c3065d16000737ebfd5c42e3f020c0074a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="createproperty-task"></a>CreateProperty, tâche
Remplit les propriétés avec les valeurs passées. Ceci permet la copie des valeurs d’une propriété ou d’une chaîne vers une autre.  
  
## <a name="attributes"></a>Attributs  
 Le tableau ci-dessous décrit les paramètres de la tâche `CreateProperty`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Value`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie la valeur à copier dans la nouvelle propriété.|  
|`ValueSetByTask`|Paramètre de sortie `String` facultatif.<br /><br /> Contient la même valeur que le paramètre `Value`. Utilisez ce paramètre seulement quand vous voulez éviter que la propriété de sortie soit définie par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] quand il ignore la cible englobante en raison du fait que les sorties sont à jour.|  
  
## <a name="remarks"></a>Remarques  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Classe de base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche `CreateProperty` pour créer la propriété `NewFile` en utilisant la combinaison des valeurs des propriétés `SourceFilename` et `SourceFileExtension`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 Après l’exécution du projet, la valeur de la propriété `NewFile` est `Module1.vb`.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)   
 [Tâches](../msbuild/msbuild-tasks.md)