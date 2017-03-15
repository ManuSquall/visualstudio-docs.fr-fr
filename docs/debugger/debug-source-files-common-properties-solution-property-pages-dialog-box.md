---
title: "Fichiers sources pour le d&#233;bogage, Propri&#233;t&#233;s communes, bo&#238;te de dialogue Pages de propri&#233;t&#233;s de Solution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.options.FindSource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Fichiers sources pour le débogage (page de propriétés)"
  - "débogage (Visual Studio), spécification des fichiers sources et de symboles"
  - "fichiers sources, spécification dans le débogueur"
  - "débogueur, fichiers sources"
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Fichiers sources pour le d&#233;bogage, Propri&#233;t&#233;s communes, bo&#238;te de dialogue Pages de propri&#233;t&#233;s de Solution
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette page de propriétés spécifie à quel endroit le débogueur recherchera les fichiers sources lors du débogage de la solution.  
  
 Pour accéder à la page de propriétés **Fichiers sources pour le débogage**, cliquez avec le bouton droit sur votre solution dans l'**Explorateur de solutions**, puis sélectionnez **Propriétés** dans le menu contextuel.  Développez le dossier **Propriétés communes**, puis cliquez sur la page **Fichiers sources pour le débogage**.  
  
 **Répertoires contenant du code source**  
 Contient la liste des répertoires dans lesquels le débogueur recherche les fichiers sources lors du débogage de la solution.  Les sous\-répertoires des dossiers spécifiés sont également récupérés.  
  
 **Ne pas rechercher ces fichiers sources**  
 Entrez le nom des fichiers que vous souhaitez soustraire à la lecture du débogueur.  Si le débogueur trouve un de ces fichiers dans un des répertoires spécifiés précédemment, il l'ignore.  Si la boîte de dialogue **Rechercher la source** s'affiche pendant que vous déboguez et que vous cliquez sur **Annuler**, le fichier que vous recherchiez se trouve ajouté à cette liste de sorte que le débogueur ne continue pas à rechercher ce fichier.  
  
## Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Paramètres et préparation du débogage](../debugger/debugger-settings-and-preparation.md)