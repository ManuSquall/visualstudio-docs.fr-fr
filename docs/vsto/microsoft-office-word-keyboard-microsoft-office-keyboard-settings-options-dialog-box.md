---
title: Clavier Office Word, paramètres, boîte de dialogue Options
description: Découvrez comment vous pouvez faire en sorte que Microsoft Word reçoive des commandes de touches de raccourci lorsque le document a le focus en sélectionnant le schéma de clavier dynamique.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
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
ms.openlocfilehash: bf4cfbaf23ad9c1e545af25614722cd52c493df7
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528442"
---
# <a name="microsoft-office-word-keyboard-settings-options-dialog-box"></a>Microsoft Office clavier Word, paramètres, boîte de dialogue Options
  Microsoft Office Word et Visual Studio gèrent les touches de raccourci. La même combinaison de touches de raccourci peut reposer pour différentes commandes dans Word et dans Visual Studio. Quand Word est ouvert dans un projet au niveau du document dans Visual Studio, une seule application à la fois reçoit les commandes de touches de raccourci. Par défaut, Visual Studio reçoit toutes les commandes de touches de raccourci, mais vous pouvez faire en sorte que Word les reçoit lorsque le document a le focus en sélectionnant **schéma de clavier dynamique**.

 Si vous utilisez une touche de raccourci qui n’est pas assignée à une commande de l’application qui gère actuellement les touches de raccourci, la touche de raccourci est transmise à l’autre application.

 L’option que vous sélectionnez reste en vigueur pour les projets Word jusqu’à ce que vous le modifiiez. La sélection n’affecte pas les projets Microsoft Office Excel ; vous devez apporter des modifications à Excel à l’aide des options du clavier Microsoft Office Excel.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur
 **Schéma de clavier Visual Studio** Visual Studio reçoit toutes les commandes de touches de raccourci, même si le document Word a le focus. Par exemple, si vous appuyez sur la touche de fonction **F5** alors que le document a le focus, Visual Studio démarre le débogage de votre solution.

 **Schéma de clavier dynamique** Visual Studio reçoit des commandes de touche de raccourci uniquement lorsqu’il a le focus. Lorsque le document Word a le focus, Word reçoit toutes les commandes de touches de raccourci. Par exemple, si vous appuyez sur la touche de fonction **F5** alors que le document Word a le focus, Word ouvre la boîte de dialogue **Rechercher et remplacer** avec l’onglet **atteindre** sélectionné. Si vous appuyez sur **F5** alors que Visual Studio a le focus, Visual Studio démarre le débogage de votre solution.

## <a name="see-also"></a>Voir aussi
- [Microsoft Office clavier Excel, Microsoft Office paramètres du clavier, boîte de dialogue Options](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
