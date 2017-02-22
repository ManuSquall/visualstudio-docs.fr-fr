---
title: "MSBuild Response Files | Microsoft Docs"
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
  - "response files, MSBuild"
  - "MSBuild, response files"
  - "MSBuild, .rsp files"
  - ".rsp files"
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# MSBuild Response Files
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les fichiers réponse \(.rsp\) sont des fichiers texte qui contiennent des commutateurs de ligne de commande MSBuild.exe.  Chaque commutateur peut se trouver sur une ligne distincte ou tous les commutateurs peuvent se trouver sur une seule ligne.  Les lignes de commentaires sont précédées d'un symbole **\#**.  Le commutateur **@** est utilisé pour passer un autre fichier réponse à MSBuild.exe.  
  
 Le fichier réponse automatique est un fichier .rsp spécial que MSBuild.exe utilise automatiquement lors de la génération d'un projet.  Ce fichier, MSBuild.rsp, doit se trouver dans le même répertoire que MSBuild.exe ; sinon, il restera introuvable.  Vous pouvez modifier ce fichier pour spécifier des commutateurs de ligne de commande par défaut pour MSBuild.exe.  Par exemple, si vous utilisez le même enregistreur d'événements pour chaque génération de projet, vous pouvez ajouter le commutateur **\/logger** à MSBuild.rsp. De cette façon, MSBuild.exe utilisera cet enregistreur d'événements à chaque génération de projet.  
  
## Voir aussi  
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)