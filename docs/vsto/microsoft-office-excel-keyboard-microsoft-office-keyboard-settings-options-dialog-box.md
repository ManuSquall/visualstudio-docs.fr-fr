---
title: "Clavier Microsoft Office Excel, Param&#232;tres du clavier Microsoft Office, bo&#238;te de dialogue Options | Microsoft Docs"
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
  - "VST.ExcelOptions.KeyboardMappingScheme"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "raccourcis clavier, développement Office dans Visual Studio"
ms.assetid: 2a8b9e70-66fa-4461-8039-b6d8a2fbb963
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Clavier Microsoft Office Excel, Param&#232;tres du clavier Microsoft Office, bo&#238;te de dialogue Options
  Microsoft Office Excel et Visual Studio prennent en charge des touches de raccourci.  La même combinaison de touches de raccourci peut correspondre à des commandes différentes dans Excel et dans Visual Studio.  Lorsque Excel est ouvert dans un projet au niveau du document dans Visual Studio, une seule application à la fois reçoit les commandes de touches de raccourci.  Par défaut, Visual Studio reçoit toutes les commandes générées par les touches de raccourci, mais si vous souhaitez qu'Excel les reçoive lorsque le document a le focus, sélectionnez **Schéma de clavier dynamique**.  
  
 Si vous utilisez une touche de raccourci qui n'est pas assignée à une commande dans l'application gérant les touches de raccourci, la touche de raccourci est transmise à l'autre application.  
  
 L'option que vous sélectionnez reste effective pour tous les projets Excel tant que vous ne la modifiez pas.  La sélection n'affecte pas les projets Microsoft Office Word ; pour effectuer des modifications dans Word, utilisez les options de clavier Microsoft Office Word.  
  
## Liste UIElement  
 **Schéma de clavier Visual Studio**  
 Visual Studio reçoit toutes les commandes générées par les touches de raccourci, même si Excel a le focus.  Par exemple, si vous appuyez sur la touche de fonction F5 pendant qu'Excel a le focus, Visual Studio commence à déboguer votre solution.  
  
 **Schéma de clavier dynamique**  
 Visual Studio reçoit les commandes générées par les touches de raccourci uniquement lorsqu'il a le focus.  Lorsqu'Excel a le focus, il reçoit toutes les commandes générées par les touches de raccourci.  Par exemple, si vous appuyez sur la touche de fonction F5 pendant qu'Excel a le focus, Excel ouvre la boîte de dialogue  **Atteindre**.  Si vous appuyez sur F5 pendant que Visual Studio a le focus, Visual Studio commence à déboguer votre solution.  
  
## Voir aussi  
 [Clavier Microsoft Office Word, Paramètres du clavier Microsoft Office, boîte de dialogue Options](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  