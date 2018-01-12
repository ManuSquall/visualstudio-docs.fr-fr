---
title: "Boîte de dialogue Options de clavier Microsoft Office Excel, paramètres du clavier Microsoft Office, | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
dev_langs:
- VB
- CSharp
helpviewer_keywords: keyboard shortcuts, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d52b7baf1283f986ee378c800114836da606eca8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Clavier Microsoft Office Excel, Paramètres du clavier Microsoft Office, boîte de dialogue Options
  Microsoft Office Excel et Visual Studio prennent en charge les touches de raccourci. La même combinaison de touches de raccourci peut correspondre à des commandes différentes dans Excel et dans Visual Studio. Quand Excel est ouvert dans un projet au niveau du document dans Visual Studio, une seule application à la fois reçoit les commandes de touches de raccourci. Par défaut, Visual Studio reçoit toutes les commandes de touches de raccourci, mais si vous souhaitez qu’Excel les reçoive lorsque le document a le focus en sélectionnant **schéma de clavier dynamique**.  
  
 Si vous utilisez la touche de raccourci qui n’est pas affectée à une commande dans l’application qui gère les touches de raccourci actuellement, la touche de raccourci est passée à l’autre application.  
  
 L’option que vous sélectionnez reste en vigueur pour les projets Excel tant que vous le modifiez. La sélection n’affecte pas les projets Microsoft Office Word ; Vous devez modifiez pour Word en utilisant les options du clavier Microsoft Office Word.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Schéma de clavier Visual Studio**  
 Visual Studio reçoit toutes les commandes de touches de raccourci, même si Excel a le focus. Par exemple, si vous appuyez sur la touche de fonction F5 pendant qu’Excel a le focus, Visual Studio commence à déboguer votre solution.  
  
 **Schéma de clavier dynamique**  
 Visual Studio reçoit les commandes de touches de raccourci uniquement lorsqu’il a le focus. Lorsqu’Excel a le focus, Excel reçoit toutes les commandes de touches de raccourci. Par exemple, si vous appuyez sur la touche de fonction F5 pendant qu’Excel a le focus, Excel ouvre le **atteindre** boîte de dialogue. Si vous appuyez sur F5 pendant que Visual Studio a le focus, Visual Studio démarre le débogage de votre solution.  
  
## <a name="see-also"></a>Voir aussi  
 [Clavier Microsoft Office Word, Paramètres du clavier Microsoft Office, boîte de dialogue Options](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  