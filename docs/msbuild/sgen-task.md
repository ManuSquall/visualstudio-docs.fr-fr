---
title: "SGen Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#SGen"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "SGen task [MSBuild]"
  - "MSBuild, SGen task"
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# SGen Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crée un assembly de sérialisation XML pour les types dans l'assembly spécifié.  Cette tâche encapsule l'outil XML Serializer Generator \(Sgen.exe\).  Pour plus d'informations, consultez [Outil XML Serializer Generator \(Sgen.exe\)](../Topic/XML%20Serializer%20Generator%20Tool%20\(Sgen.exe\).md).  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `SGen`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`BuildAssemblyName`|Paramètre `String` obligatoire.<br /><br /> Assembly pour lequel le code de sérialisation doit être généré.|  
|`BuildAssemblyPath`|Paramètre `String` obligatoire.<br /><br /> Chemin d'accès de l'assembly pour lequel le code de sérialisation doit être généré.|  
|`DelaySign`|Paramètre `Boolean` facultatif.<br /><br /> La valeur `true` indique que vous souhaitez obtenir un assembly complètement signé.  La valeur `false` spécifie que vous souhaitez uniquement placer la clé publique dans l'assembly.<br /><br /> Ce paramètre n'a aucun effet sauf lorsqu'il est utilisé avec le paramètre `KeyFile` ou `KeyContainer`.|  
|`KeyContainer`|Paramètre `String` facultatif.<br /><br /> Spécifie un conteneur qui contient une paire de clés.  Cela signera l'assembly en insérant une clé publique dans le manifeste d'assembly.  La tâche signe ensuite l'assembly final à l'aide la clé privée.|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Spécifie une paire de clés ou une clé publique à utiliser pour signer un assembly.  Le compilateur insère la clé publique dans le manifeste d'assembly, puis signe l'assembly final avec la clé privée.|  
|`Platform`|Paramètre `String` facultatif.<br /><br /> Obtient ou définit la plateforme de compilateur utilisée pour générer l'assembly de sortie.  Ce paramètre peut avoir les valeurs `x86`, `x64` ou `anycpu`.  La valeur par défaut est `anycpu`.|  
|`References`|Paramètre `String[]` facultatif.<br /><br /> Spécifie les assemblys référencés par les types qui requièrent la sérialisation XML.|  
|`SdkToolsPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin d'accès des outils du Kit de développement logiciel, comme resgen.exe.|  
|`SerializationAssembly`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient l'assembly de sérialisation généré.|  
|`SerializationAssemblyName`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom de l'assembly de sérialisation généré.|  
|`ShouldGenerateSerializer`|Paramètre `Boolean` obligatoire.<br /><br /> Si la valeur est `true`, la tâche SGen doit générer un assembly de sérialisation.|  
|`Timeout`|Paramètre `Int32` facultatif.<br /><br /> Spécifie la durée, en millisecondes, après laquelle la tâche exécutable est terminée.  La valeur par défaut est `Int.MaxValue`, indiquant qu'il n'existe aucun délai d'attente.|  
|`ToolPath`|Paramètre `String` facultatif.<br /><br /> Spécifie l'emplacement à partir duquel la tâche charge le fichier exécutable sous\-jacent \(sgen.exe\).  Si ce paramètre n'est pas spécifié, la tâche utilise le chemin d'accès d'installation du Kit de développement logiciel qui correspond à la version de l'infrastructure exécutant [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`Types`|Paramètre `String[]` facultatif.<br /><br /> Obtient ou définit une liste de type spécifiques pour lesquels le code de sérialisation doit être généré.  SGen générera le code de sérialisation uniquement pour ces types.|  
|`UseProxyTypes`|Paramètre `Boolean` obligatoire.<br /><br /> Si la valeur est `true`, la tâche SGen génère le code de sérialisation uniquement pour les types de proxy de service Web XML.|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.ToolTask>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)