---
title: Clavier Office Excel, paramètres, boîte de dialogue Options
description: Découvrez comment vous pouvez faire en sorte que Microsoft Excel reçoive des commandes de touches de raccourci lorsque le document a le focus en sélectionnant le schéma de clavier dynamique.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: b3422cb53fb454b3585e0b8ba936ce692dfc68a4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525313"
---
# <a name="microsoft-office-excel-keyboard-settings-options-dialog-box"></a>Microsoft Office clavier Excel, paramètres, boîte de dialogue Options
  Microsoft Office Excel et Visual Studio gèrent les touches de raccourci. La même combinaison de touches de raccourci peut reposer pour différentes commandes dans Excel et dans Visual Studio. Quand Excel est ouvert dans un projet au niveau du document dans Visual Studio, une seule application à la fois reçoit les commandes de touches de raccourci. Par défaut, Visual Studio reçoit toutes les commandes de touches de raccourci, mais vous pouvez faire en sorte qu’Excel les reçoit lorsque le document a le focus en sélectionnant **schéma de clavier dynamique**.

 Si vous utilisez une touche de raccourci qui n’est pas assignée à une commande de l’application qui gère actuellement les touches de raccourci, la touche de raccourci est transmise à l’autre application.

 L’option que vous sélectionnez reste en vigueur pour les projets Excel jusqu’à ce que vous le modifiiez. La sélection n’affecte pas les projets Microsoft Office Word ; vous devez apporter des modifications à Word à l’aide des options de clavier Microsoft Office Word.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur
 **Schéma de clavier Visual Studio** Visual Studio reçoit toutes les commandes de touches de raccourci, même si Excel a le focus. Par exemple, si vous appuyez sur la touche de fonction **F5** alors qu’Excel a le focus, Visual Studio démarre le débogage de votre solution.

 **Schéma de clavier dynamique** Visual Studio reçoit des commandes de touche de raccourci uniquement lorsqu’il a le focus. Lorsqu’Excel a le focus, Excel reçoit toutes les commandes de touches de raccourci. Par exemple, si vous appuyez sur la touche de fonction **F5** alors qu’Excel a le focus, Excel ouvre la boîte **de dialogue atteindre** . Si vous appuyez sur **F5** alors que Visual Studio a le focus, Visual Studio démarre le débogage de votre solution.

## <a name="see-also"></a>Voir aussi
- [Microsoft Office clavier Word, Microsoft Office paramètres du clavier, boîte de dialogue Options](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
