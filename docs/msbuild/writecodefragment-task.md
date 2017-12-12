---
title: "WriteCodeFragment, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 4bc15b18a5c29f77f9d3e62c281222dda0cdc347
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="writecodefragment-task"></a>WriteCodeFragment, tâche
Génère un fichier de code temporaire à partir du fragment de code généré spécifié. Ne supprime pas le fichier.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `WriteCodeFragment` .  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AssemblyAttributes`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Description des attributs à écrire. La valeur `Include` de l’élément correspond au nom de type complet de l’attribut, par exemple, « System.AssemblyVersionAttribute ».<br /><br /> Chaque métadonnée correspond à la paire nom-valeur d’un paramètre, qui doit être de type `String`. Certains attributs autorisent uniquement les arguments de constructeur. Toutefois, vous pouvez utiliser ces arguments dans n’importe quel attribut. Pour définir les attributs de constructeur positionnel, utilisez les noms de métadonnées qui ressemblent à « _Parameter1 », « _Parameter2 » , etc.<br /><br /> Vous ne pouvez pas ignorer un index de paramètre.|  
|`Language`|Paramètre `String` requis.<br /><br /> Spécifie le langage du code à générer.<br /><br /> `Language` peut être n’importe quel langage disposant d’un fournisseur CodeDom, par exemple, « C# » ou « VisualBasic ». Le fichier émis porte l’extension de nom de fichier par défaut du langage en question.|  
|`OutputDirectory`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le dossier de destination du code généré, en général le dossier intermédiaire.|  
|`OutputFile`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le chemin du fichier qui a été généré. Si ce paramètre est défini à l’aide d’un nom de fichier, le dossier de destination est ajouté devant le nom de fichier. S’il est défini à l’aide d’une racine, le dossier de destination est ignoré.<br /><br /> Si ce paramètre n’est pas défini, le nom du fichier de sortie est constitué du nom du dossier de destination, d’un nom de fichier arbitraire et de l’extension de nom de fichier par défaut du langage spécifié.|  
  
## <a name="remarks"></a>Remarques  
 En plus des paramètres répertoriés dans le tableau, cette tâche comprend des paramètres qu’elle hérite de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches MSBuild](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)