---
title: Procédures pas à pas personnalisation de l’interface utilisateur Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes, walkthroughs
- smart documents, walkthroughs
- walkthroughs [Office development in Visual Studio], smart tags
- walkthroughs [Office development in Visual Studio], action panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 95561f1404da1efd71ff3418f9154392f393795c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977885"
---
# <a name="office-ui-customization-walkthroughs"></a>Procédures pas à pas personnalisation de l’interface utilisateur Office
  Les procédures pas à pas suivantes montrent comment personnaliser l’interface utilisateur des applications Microsoft Office à l’aide des personnalisations au niveau du document et des compléments VSTO.

## <a name="actions-pane-walkthroughs"></a>Procédures pas à pas volet d’actions
- [Procédure pas à pas : Insérer du texte dans un document à partir d’un volet actions](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md) montre comment créer un volet actions dans un document Word. Le volet Actions contient deux contrôles qui envoient l’entrée utilisateur au document.

- [Procédure pas à pas : Lier des données aux contrôles dans un volet actions Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md) montre comment lier des contrôles dans un volet actions dans Word à des données. Les contrôles illustrent une relation Maître/Détail entre des tables dans une base de données SQL Server.

- [Procédure pas à pas : Lier des données aux contrôles dans un volet actions Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md) décrit comment ajouter des contrôles qui sont liés à une source de données à un volet actions dans Excel.

## <a name="custom-task-pane-walkthroughs"></a>Procédures pas à pas volet de tâches personnalisé
- [Procédure pas à pas : Automatiser une application à partir d’un volet Office personnalisé](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md) montre comment créer un volet Office personnalisé contenant un contrôle qui automatise l’application hôte lorsque l’utilisateur clique sur le contrôle.

- [Procédure pas à pas : Synchroniser un volet Office personnalisé avec un bouton de ruban](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md) montre comment créer un volet Office personnalisé que les utilisateurs peuvent masquer ou afficher en cliquant sur un bouton bascule du ruban.

- [Procédure pas à pas : Afficher les volets de tâches personnalisés avec des messages électroniques dans Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md) montre comment afficher une instance unique d’un volet de tâches personnalisé avec chaque message électronique créé ou ouvert dans Outlook.

## <a name="ribbon-walkthroughs"></a>Procédures pas à pas de ruban
- [Procédure pas à pas : Créer un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md) montre comment créer un onglet de ruban personnalisé à l’aide du Concepteur de ruban. Cet onglet contient un bouton qui permet de masquer ou d’afficher un volet Actions.

- [Procédure pas à pas : Mettre à jour les contrôles sur un ruban lors de l’exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md) montre comment utiliser le modèle objet de ruban pour mettre à jour les contrôles sur un ruban après le chargement du ruban dans l’application Office.

- [Procédure pas à pas : Créer un onglet personnalisé à l’aide du ruban XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md) montre comment créer un onglet de ruban personnalisé à l’aide de ruban XML au lieu d’utiliser le Concepteur de ruban.

## <a name="controls-on-word-documents"></a>Contrôles sur des documents Word
- [Procédure pas à pas : Ajouter des contrôles à un document lors de l’exécution dans un complément VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md) montre comment ajouter des contrôles à un document en utilisant un complément, VSTO.

- [Procédure pas à pas : Modifier la mise en forme du document à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md) montre comment modifier la mise en forme dans un document Word à l’aide des cases à cocher dans une personnalisation au niveau du document.

- [Procédure pas à pas : Afficher du texte dans une zone de texte dans un document à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md) illustre l’utilisation des boutons et des zones de texte dans les documents Word.

- [Procédure pas à pas : Mettre à jour d’un graphique dans un document à l’aide de cases d’option](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md) montre comment modifier les styles de graphique dans un document Word à l’aide de cases d’option dans une personnalisation au niveau du document.

## <a name="controls-on-excel-worksheets"></a>Contrôles sur des feuilles de calcul Excel
- [Procédure pas à pas : Ajouter des contrôles à une feuille de calcul lors de l’exécution dans un projet de complément VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) montre comment ajouter des contrôles à une feuille de calcul en utilisant un VSTO Add-in.

- [Procédure pas à pas : Modifier la mise en forme de feuille de calcul à l’aide de contrôles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md) illustre les principes fondamentaux de l’utilisation des cases à cocher dans une feuille de calcul Excel pour modifier la mise en forme.

- [Procédure pas à pas : Afficher du texte dans une zone de texte dans une feuille de calcul à l’aide d’un bouton](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md) illustre les principes fondamentaux de l’utilisation des boutons et des zones de texte sur des feuilles de calcul Excel.

- [Procédure pas à pas : Mettre à jour d’un graphique dans une feuille de calcul à l’aide de cases d’option](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md) présente les notions de base de la modification des styles de graphique à l’aide de cases d’option sur une feuille de calcul Excel.

## <a name="see-also"></a>Voir aussi
- [Procédures pas à pas utilisant Word](../vsto/walkthroughs-using-word.md)
- [Procédures pas à pas utilisant Excel](../vsto/walkthroughs-using-excel.md)
- [Données dans les guides de solutions Office](../vsto/data-in-office-solutions-walkthroughs.md)
- [Procédures pas à pas de déploiement et de sécurité](../vsto/security-and-deployment-walkthroughs.md)
- [Prise en main &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Tâches courantes dans la programmation Office](../vsto/common-tasks-in-office-programming.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
