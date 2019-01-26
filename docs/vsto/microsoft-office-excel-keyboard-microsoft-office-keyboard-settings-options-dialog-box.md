---
title: Boîte de dialogue Options de clavier Microsoft Office Excel, paramètres du clavier Microsoft Office,
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4dcf80961fa035145aa32d32636d9645f8c61ec4
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876146"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Boîte de dialogue Options de clavier Microsoft Office Excel, paramètres du clavier Microsoft Office,
  Microsoft Office Excel et Visual Studio prennent en charge les touches de raccourci. La même combinaison de touches de raccourci peut correspondre à des commandes différentes dans Excel et dans Visual Studio. Quand Excel est ouvert dans un projet au niveau du document dans Visual Studio, qu’une seule application à la fois reçoit les commandes de touches de raccourci. Par défaut, Visual Studio reçoit toutes les commandes de touches de raccourci, mais vous souhaitez qu’Excel les reçoive lorsque le document a le focus en sélectionnant **schéma de clavier dynamique**.  
  
 Si vous utilisez une touche de raccourci qui n’est pas affectée à une commande dans l’application qui gère les touches de raccourci actuellement, la touche de raccourci est passée à l’autre application.  
  
 L’option que vous sélectionnez restera en vigueur pour les projets Excel jusqu'à ce que vous le changiez. La sélection n’affecte pas les projets Microsoft Office Word ; Vous devez vous des modifications dans Word en utilisant les options de clavier Microsoft Office Word.  
  
## <a name="uielement-list"></a>Liste UIElement  
 **Schéma de clavier Visual Studio**  
 Visual Studio reçoit toutes les commandes de touches de raccourci, même si Excel a le focus. Par exemple, si vous appuyez sur la touche de fonction **F5** quand Excel a le focus, Visual Studio démarre le débogage de votre solution.  
  
 **Schéma de clavier dynamique**  
 Visual Studio reçoit les commandes de touches de raccourci uniquement lorsque celui-ci a le focus. Lorsqu’Excel a le focus, Excel reçoit toutes les commandes de touches de raccourci. Par exemple, si vous appuyez sur la touche de fonction **F5** quand Excel a le focus, Excel s’ouvre le **atteindre** boîte de dialogue. Si vous appuyez sur **F5** tandis que Visual Studio a le focus, Visual Studio démarre le débogage de votre solution.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Options de clavier Microsoft Office Word, paramètres du clavier Microsoft Office,](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
