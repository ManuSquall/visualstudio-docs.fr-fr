---
title: "Clavier Microsoft Office Word, Param&#232;tres du clavier Microsoft Office, bo&#238;te de dialogue Options | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard"
  - "VST.WordOptions.KeyboardMappingScheme"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "raccourcis clavier, développement Office dans Visual Studio"
ms.assetid: d98edaab-846a-4baa-b190-702b1134754c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Clavier Microsoft Office Word, Param&#232;tres du clavier Microsoft Office, bo&#238;te de dialogue Options
  Microsoft Office Word et Visual Studio prennent en charge les touches de raccourci.  La même combinaison de touches de raccourci peut correspondre à des commandes différentes dans Word et dans Visual Studio.  Lorsque Word est ouvert dans un projet au niveau du document dans Visual Studio, une seule application à la fois reçoit les commandes de touches de raccourci.  Par défaut, Visual Studio reçoit toutes les commandes générées par les touches de raccourci, mais si vous souhaitez que Word les reçoive lorsque le document a le focus, sélectionnez **Schéma de clavier dynamique**.  
  
 Si vous utilisez une touche de raccourci qui n'est pas assignée à une commande dans l'application gérant les touches de raccourci, la touche de raccourci est transmise à l'autre application.  
  
 L'option que vous sélectionnez reste effective pour tous les projets Word tant que vous ne la modifiez pas.  La sélection n'affecte pas les projets Microsoft Office Excel ; pour apporter une modification dans Excel, utilisez les options de clavier Microsoft Office Excel.  
  
## Liste UIElement  
 **Schéma de clavier Visual Studio**  
 Visual Studio reçoit toutes les commandes générées par les touches de raccourci, même si le document Word a le focus.  Par exemple, si vous appuyez sur la touche de fonction F5 pendant que le document a le focus, Visual Studio commence à déboguer votre solution.  
  
 **Schéma de clavier dynamique**  
 Visual Studio reçoit les commandes générées par les touches de raccourci uniquement lorsqu'il a le focus.  Lorsque le document Word a le focus, Word reçoit toutes les commandes générées par les touches de raccourci.  Par exemple, si vous appuyez sur la touche de fonction F5 pendant que le document Word a le focus, Word ouvre la boîte de dialogue **Rechercher et remplacer** avec l'onglet **Atteindre** sélectionné.  Si vous appuyez sur F5 pendant que Visual Studio a le focus, Visual Studio commence à déboguer votre solution.  
  
## Voir aussi  
 [Clavier Microsoft Office Excel, Paramètres du clavier Microsoft Office, boîte de dialogue Options](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  