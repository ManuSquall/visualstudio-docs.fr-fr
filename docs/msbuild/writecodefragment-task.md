---
title: "WriteCodeFragment Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, WriteCodeFragment task"
  - "WriteCodeFragment task [MSBuild]"
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# WriteCodeFragment Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Génère un fichier de code temporaire du fragment de code généré spécifié.  N'efface pas le fichier.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `WriteCodeFragment`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AssemblyAttributes`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Description des attributs à écrire.  La valeur `Include` de l'élément est le nom de type complet de l'attribut, par exemple, « System.AssemblyVersionAttribute ».<br /><br /> Chaque métadonnée est la paire nom\-valeur d'un paramètre, qui doit être de type `String`.  Certains attributs autorisent uniquement les arguments de constructeur de position.  Vous pouvez cependant utiliser ces arguments dans n'importe quel attribut.  Pour définir les attributs de constructeur de position, utilisez des noms de métadonnées qui ressemblent à "\_Parameter1", "\_Parameter2", et ainsi de suite.<br /><br /> Un index de paramètre ne peut pas être ignoré.|  
|`Language`|Paramètre `String` obligatoire.<br /><br /> Spécifie le langage du code à générer.<br /><br /> `Language` peut être n'importe quel langage pour lequel un fournisseur CodeDom est disponible, par exemple, "C\#" ou "VisualBasic".  Le fichier émis aura l'extension de nom de fichier par défaut pour ce langage.|  
|`OutputDirectory`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le dossier de destination du code généré, en général le dossier intermédiaire.|  
|`OutputFile`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le chemin d'accès du fichier qui a été généré.  Si ce paramètre est défini à l'aide d'un nom de fichier, le dossier de destination est ajouté au début du nom de fichier.  Si la définition est effectuée à l'aide d'une racine, le dossier de destination est ignoré.<br /><br /> Si ce paramètre n'est pas défini, le nom du fichier de sortie correspond au dossier de destination, à un nom de fichier arbitraire et à l'extension de nom de fichier par défaut pour le langage spécifié.|  
  
## Notes  
 En plus des paramètres répertoriés dans le tableau, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle\-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)