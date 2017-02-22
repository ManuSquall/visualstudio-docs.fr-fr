---
title: "RC Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions"
  - "vc.task.rc"
  - "VC.Project.VCResourceCompilerTool.SuppressStartupBanner"
  - "VC.Project.VCResourceCompilerTool.NullTerminateStrings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "RC task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), RC task"
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# RC Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Encapsule l'outil Compilateur de ressources Microsoft Windows, rc.exe.  La tâche **RC** compile des ressources, telles que des curseurs, des icônes, des bitmaps, des boîtes de dialogue et des polices, dans un fichier de ressources \(.res\).  Pour plus d'informations, consultez « Compilateur de ressources » sur le site [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche RC.  La plupart des paramètres de tâche, et quelques jeux de paramètres, correspondent à une option de ligne de commande.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|Paramètre **String\[\]** facultatif.<br /><br /> Ajoute un répertoire à la liste des répertoires dans lesquels sont recherchés des fichiers Include.<br /><br /> Pour plus d'informations, consultez l'option **\/I** dans [Utilisation de RC \(Ligne de commande RC\) \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=155730) sur le site Web MSDN.|  
|**AdditionalOptions**|Paramètre **String** facultatif.<br /><br /> Une liste d'exemple de l'optionsor de la ligne de commande, **"***\/option1 \/option2 \/option\#*".  Utilisez ce paramètre pour spécifier des options de ligne de commande qui ne sont pas représentées par un  autre paramètre de tâche **RC**.<br /><br /> Pour plus d'informations, consultez les options pour [Utilisation de RC \(Ligne de commande RC\)](http://go.microsoft.com/fwlink/?LinkId=155730) sur le site Web MSDN.|  
|**Culture**|Paramètre **String** facultatif.<br /><br /> Spécifie un ID de paramètres régionaux qui représente la culture utilisée dans les ressources.<br /><br /> Pour plus d'informations, consultez l'option **\/l** dans [Utilisation de RC \(Ligne de commande RC\) \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=155730) sur le site Web MSDN.|  
|**IgnoreStandardIncludePath**|Paramètre **Boolean** facultatif.<br /><br /> Si `true`, empêche le compilateur de ressources de vérifier la variable d'environnement INCLUDE lorsqu'il recherche des fichiers d'en\-tête ou des fichiers de ressources.<br /><br /> Pour plus d'informations, consultez l'option **\/x** dans [Utilisation de RC \(Ligne de commande RC\) \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=155730) sur le site Web MSDN.|  
|**NullTerminateStrings**|Paramètre **Boolean** facultatif.<br /><br /> Si `true`, toutes les chaînes dans le tableau de chaînes sont terminées par null.<br /><br /> Pour plus d'informations, consultez l'option **\/n** dans [Utilisation de RC \(Ligne de commande RC\) \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=155730) sur le site Web MSDN.|  
|**PreprocessorDefinitions**|Paramètre **String\[\]** facultatif.<br /><br /> Définissez un ou plusieurs symboles de préprocesseur pour le compilateur de ressources.  Spécifiez une liste de symboles de macro.<br /><br /> Pour plus d'informations, consultez l'option **\/d** dans [Utilisation de RC \(Ligne de commande RC\) \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=155730) sur le site Web MSDN.  Consultez également **UndefinePreprocessorDefinitions** dans ce tableau.|  
|**ResourceOutputFileName**|Paramètre **String** facultatif.<br /><br /> Spécifie le nom du fichier de ressources.  Spécifiez un nom de fichier de ressources.<br /><br /> Pour plus d'informations, consultez l'option **\/fo** dans [Utilisation de RC \(Ligne de commande RC\) \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=155730) sur le site Web MSDN.|  
|**ShowProgress**|Paramètre **Boolean** facultatif.<br /><br /> Si `true`, affiche des messages qui font un rapport sur la progression du compilateur.<br /><br /> Pour plus d'informations, consultez l'option **\/v** dans [Utilisation de RC \(Ligne de commande RC\) \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=155730) sur le site Web MSDN.|  
|**Source**|Paramètre `ITaskItem[]` obligatoire.<br /><br /> Définit un tableau des éléments de fichier source MSBuild qui peuvent être consommés et peuvent être émis par les tâches.|  
|**SuppressStartupBanner**|Paramètre **Boolean** facultatif.<br /><br /> Si `true`, empêche l'affichage du copyright et du numéro de version lorsque la tâche démarre.<br /><br /> Pour plus d'informations, tapez l'option de ligne de commande **\/?** puis consultez l'option **\/nologo**.|  
|**TrackerLogDirectory**|Paramètre **String** facultatif.<br /><br /> Spécifie le répertoire des journaux de Tracker.|  
|**UndefinePreprocessorDefinitions**|Annule la définition d'un symbole de préprocesseur.<br /><br /> Pour plus d'informations, consultez l'option **\/u** dans [Utilisation de RC \(Ligne de commande RC\) \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=155730) sur le site Web MSDN.  Consultez également **PreprocessorDefinitions** dans ce tableau.|  
  
## Notes  
  
## Voir aussi  
 [Task Reference](../msbuild/msbuild-task-reference.md)