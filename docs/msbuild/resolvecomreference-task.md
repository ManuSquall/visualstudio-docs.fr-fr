---
title: "ResolveComReference Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, ResolveCOMReference task"
  - "ResolveCOMReference task [MSBuild]"
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# ResolveComReference Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilise une liste d'un ou plusieurs noms de bibliothèques de types ou de fichiers .tlb et résout ces bibliothèques de types aux emplacements sur le disque.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `ResolveCOMReference`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`DelaySign`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, place la clé publique dans l'assembly.  Si la valeur est `false`, signe complètement l'assembly.|  
|`EnvironmentVariables`|Paramètre `String[]` facultatif.<br /><br /> Tableau de paires de variables d'environnement, séparées par un signe égal.  Ces variables sont passées aux fichiers tlbimp.exe et aximp.exe générés en plus du bloc environnement normal ou en remplacement de celui\-ci.|  
|`ExecuteAsTool`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, exécute tlbimp.exe et aximp.exe à partir de la version cible du .NET Framework appropriée hors processus pour générer les assemblys de wrappers nécessaires.  Ce paramètre permet le multi\-ciblage.|  
|`IncludeVersionInInteropName`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la version de la typelib sera incluse dans le nom du wrapper.  La valeur par défaut est `false`.|  
|`KeyContainer`|Paramètre `String` facultatif.<br /><br /> Spécifie un conteneur qui détient une paire de clés publique\/privée<br /><br /> .|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Spécifie un élément qui contient une paire de clés publique\/privée<br /><br /> .|  
|`NoClassMembers`|Paramètre `Boolean` facultatif.|  
|`ResolvedAssemblyReferences`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les références d'assembly résolues.|  
|`ResolvedFiles`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie les fichiers qualifiés complets sur le disque qui correspondent aux emplacements physiques des bibliothèques de types fournies comme entrée pour cette tâche.|  
|`ResolvedModules`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.|  
|`SdkToolsPath`|Paramètre [String](assetId:///String?qualifyHint=False&autoUpgrade=True) facultatif.<br /><br /> Si `ExecuteAsTool` a la valeur `true`, ce paramètre doit être défini sur le chemin d'accès des outils du Kit de développement logiciel pour la version de .NET Framework ciblée.|  
|`StateFile`|Paramètre assetId:///String?qualifyHint=False&autoUpgrade=True facultatif.<br /><br /> Spécifie le fichier cache pour les horodatages de composant COM.  En cas d'absence, chaque exécution régénère l'ensemble des wrappers.|  
|`TargetFrameworkVersion`|Paramètre assetId:///String?qualifyHint=False&autoUpgrade=True facultatif.<br /><br /> Spécifie la version cible de .Net Framework pour un projet.<br /><br /> La valeur par défaut est `String.Empty`.  ce qui signifie qu'il n'y a pas de filtrage de référence basé sur la version cible de .NET Framework.|  
|`TargetProcessorArchitecture`|Paramètre assetId:///String?qualifyHint=False&autoUpgrade=True facultatif.<br /><br /> Spécifie l'architecture de processeur cible par défaut.  Passé à l'indicateur de tlbimp.exe \/ de l'ordinateur après la translation.<br /><br /> La valeur du paramètre doit faire partie de <xref:Microsoft.Build.Utilities.ProcessorArchitecture>.|  
|`TypeLibFiles`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Spécifie le chemin d'accès des bibliothèques de types aux références COM.  Les éléments inclus dans ce paramètre peuvent contenir des métadonnées d'élément.  Pour plus d'informations, consultez la section « Métadonnées d'élément TypeLibFiles » ci\-dessous.|  
|`TypeLibNames`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Spécifie les noms de bibliothèques de types à résoudre.  Les éléments inclus dans ce paramètre doivent contenir des métadonnées d'élément.  Pour plus d'informations, consultez la section « Métadonnées d'élément TypeLibNames » ci\-dessous.|  
|`WrapperOutputDirectory`|Paramètre `String` facultatif.<br /><br /> Emplacement de l'assembly d'interopérabilité généré sur le disque.  Si ces métadonnées d'élément ne sont pas spécifiées, la tâche utilise le chemin d'accès absolu du répertoire contenant le fichier projet.|  
  
## Notes  
  
## Métadonnées d'élément TypeLibNames  
 Le tableau suivant décrit les métadonnées d'élément disponibles pour les éléments passés au paramètre `TypeLibNames`.  
  
|Métadonnées|Description|  
|-----------------|-----------------|  
|`GUID`|Métadonnées d'élément requises.<br /><br /> GUID de la bibliothèque de types.  Si ces métadonnées d'élément ne sont pas spécifiées, la tâche échoue.|  
|`VersionMajor`|Métadonnées d'élément requises.<br /><br /> Version principale de la bibliothèque de types.  Si ces métadonnées d'élément ne sont pas spécifiées, la tâche échoue.|  
|`VersionMinor`|Métadonnées d'élément requises.<br /><br /> Version secondaire de la bibliothèque de types.  Si ces métadonnées d'élément ne sont pas spécifiées, la tâche échoue.|  
|`LocaleIdentifier`|Métadonnées d'élément facultatives.<br /><br /> Identificateur de paramètres régionaux \(ou LCID\) de la bibliothèque de types.  Il s'agit d'une valeur 32 bits qui identifie le langage humain préféré pour un utilisateur, une région ou une application.  Si ces métadonnées d'élément ne sont pas spécifiées, la tâche utilise la valeur par défaut "0" comme identificateur de paramètres régionaux.|  
|`WrapperTool`|Métadonnées d'élément facultatives.<br /><br /> Spécifie l'outil wrapper utilisé afin de générer le wrapper d'assembly pour cette bibliothèque de types.  Si ces métadonnées d'élément ne sont pas spécifiées, la tâche utilise l'outil wrapper par défaut "tlbimp".  Les choix disponibles qui ne respectent pas la casse pour les typelibs sont les suivants :<br /><br /> -   `Primary` : Utilisez cet outil wrapper lorsque vous souhaitez employer un assembly PIA \(Primary Interop Assembly\) déjà généré pour le composant COM.  Lorsque vous utilisez cet outil wrapper, ne spécifiez pas de répertoire de sortie de wrapper car cela provoquerait l'échec de la tâche.<br />-   `TLBImp` : Utilisez cet outil wrapper lorsque vous souhaitez générer un assembly d'interopérabilité pour le composant COM.<br />-   `AXImp`: Utilisez cet outil wrapper lorsque vous souhaitez générer un assembly d'interopérabilité pour un contrôle ActiveX.|  
  
## Métadonnées d'élément TypeLibFiles  
 Le tableau suivant décrit les métadonnées d'élément disponibles pour les éléments passés au paramètre `TypeLibFiles`.  
  
|Métadonnées|Description|  
|-----------------|-----------------|  
|`WrapperTool`|Métadonnées d'élément facultatives.<br /><br /> Spécifie l'outil wrapper utilisé afin de générer le wrapper d'assembly pour cette bibliothèque de types.  Si ces métadonnées d'élément ne sont pas spécifiées, la tâche utilise l'outil wrapper par défaut "tlbimp".  Les choix disponibles qui ne respectent pas la casse pour les typelibs sont les suivants :<br /><br /> -   `Primary` : Utilisez cet outil wrapper lorsque vous souhaitez employer un assembly PIA \(Primary Interop Assembly\) déjà généré pour le composant COM.  Lorsque vous utilisez cet outil wrapper, ne spécifiez pas de répertoire de sortie de wrapper car cela provoquerait l'échec de la tâche.<br />-   `TLBImp` : Utilisez cet outil wrapper lorsque vous souhaitez générer un assembly d'interopérabilité pour le composant COM.<br />-   `AXImp`: Utilisez cet outil wrapper lorsque vous souhaitez générer un assembly d'interopérabilité pour un contrôle ActiveX.|  
  
> [!NOTE]
>  Plus vous donnez d'informations précises sur une bibliothèque de types, plus la tâche sera en mesure de résoudre le fichier correct sur le disque.  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Utilities.Task>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [Task Base Class](../msbuild/task-base-class.md).  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)