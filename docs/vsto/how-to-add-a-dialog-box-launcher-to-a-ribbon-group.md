---
title: 'Comment : ajouter un lanceur de boîte de dialogue à un groupe de ruban'
description: Vous pouvez ajouter un lanceur de boîte de dialogue à n’importe quel groupe d’un ruban qui peut ouvrir des boîtes de dialogue ou des volets de tâches associés qui fournissent davantage d’options en rapport avec le groupe.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d8e04b7549d1b6a458f0993804946502f55f0165
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942280"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Comment : ajouter un lanceur de boîte de dialogue à un groupe de ruban
  Vous pouvez ajouter un lanceur de boîte de dialogue à n’importe quel groupe sur un ruban. Un lanceur de boîte de dialogue est une petite icône qui s’affiche dans un groupe. Les utilisateurs cliquent sur cette icône pour ouvrir des boîtes de dialogue ou des volets de tâches associés qui fournissent des options supplémentaires en rapport avec le groupe.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Pour ajouter un lanceur de boîte de dialogue à un groupe de ruban

1. Sélectionnez le fichier de code du ruban (fichier *. vb* ou *. cs* ) dans **Explorateur de solutions**.

2. Dans le menu **affichage** , cliquez sur **Concepteur**.

3. Dans le concepteur de ruban, cliquez avec le bouton droit sur n’importe quel groupe, puis cliquez sur **Ajouter DialogBoxLauncher**.

     Ajoutez du code à l' <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> événement du groupe pour ouvrir une boîte de dialogue personnalisée ou intégrée.

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)
- [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Vue d’ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Comment : exporter un ruban à partir du concepteur de ruban vers le ruban XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Comment : modifier la position d’un onglet sur le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)
- [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Comment : prendre en main la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Comment : afficher les erreurs d’interface utilisateur du complément](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procédure pas à pas : mettre à jour les contrôles sur un ruban au moment de l’exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du ruban XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
