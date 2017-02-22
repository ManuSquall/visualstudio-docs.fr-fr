---
title: "WPF MSBuild Task Reference | Microsoft Docs"
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
  - "WPF MSBuild task reference [WPF MSBuild], term/definition table"
  - "build tasks [WPF MSBuild], Microsoft build engine"
  - "build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources"
  - "WPF MSBuild task reference [WPF MSBuild]"
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# WPF MSBuild Task Reference
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le processus de génération Windows Presentation Foundation \(WPF\) étend Microsoft build engine \(MSBuild\) avec un jeu supplémentaire de tâches de génération, notamment des tâches servant à compiler le balisage et les ressources de processus.  
  
## Dans cette section  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Classe un jeu de ressources sources comme devant être incorporées dans un assembly.  Si une ressource n'est pas localisable, elle est incorporée dans l'assembly principal de l'application ; sinon, elle est incorporée dans un assembly satellite.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Génère un assembly si au moins une page [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] d'un projet fait référence à un type localement déclaré dans ce projet.  L'assembly généré est supprimé une fois le processus de génération terminé, ou lorsque le processus de génération échoue.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Retourne le répertoire du runtime [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] courant.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Convertit des fichiers projet [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] non localisables au format binaire compilé.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Exécute un deuxième passage de compilation du balisage sur les fichiers [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] qui font référence à des types dans le même projet.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Fusionne les attributs et les commentaires de localisation d'un ou plusieurs fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] au format binaire en un seul fichier pour l'intégralité de l'assembly.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Incorpore une ou plusieurs ressources \(.jpg, .ico, .bmp, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] au format binaire et autres types d'extensions\) dans un fichier .resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Vérifie, met à jour ou supprime les identificateurs uniques \(UID\), afin de localiser tous les éléments [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] inclus dans les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sources.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Ajoute l'élément  **\< hostInBrowser \/\>** dans le manifeste de l'application \(*projectname*.exe.manifest\) lorsqu'un projet [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] est généré.  
  
## Voir aussi  
 [MSBuild](http://msdn.microsoft.com/fr-fr/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)