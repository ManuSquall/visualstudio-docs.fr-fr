---
title: 'Procédure : Ajouter un lanceur de boîte de dialogue à un groupe de ruban'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aa12fdc3eea5c353071fb4a80e2c99f2f9e060c2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629948"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Procédure : Ajouter un lanceur de boîte de dialogue à un groupe de ruban
  Vous pouvez ajouter un lanceur de boîte de dialogue à n’importe quel groupe sur un ruban. Un lanceur de boîte de dialogue est une petite icône qui apparaît dans un groupe. Les utilisateurs cliquent sur cette icône pour ouvrir les boîtes de dialogue connexes ou des volets de tâches qui fournissent des options plus qui se rapportent au groupe.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Pour ajouter un lanceur de boîte de dialogue à un groupe de ruban

1.  Sélectionnez le fichier de code de ruban (*.vb* ou *.cs* fichier) dans **l’Explorateur de solutions**.

2.  Sur le **vue** menu, cliquez sur **concepteur**.

3.  Dans le Concepteur de ruban, cliquez sur n’importe quel groupe, puis cliquez sur **Ajouter DialogBoxLauncher**.

     Ajoutez le code pour le <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> événement du groupe pour ouvrir une boîte de dialogue personnalisée ou intégrée.

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Accéder au ruban lors de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)
- [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Présentation du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Guide pratique pour Exporter un ruban à partir du Concepteur de ruban vers ruban XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Guide pratique pour Modifier la position d’un onglet dans le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Guide pratique pour Personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)
- [Guide pratique pour Ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Guide pratique pour Commencer la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Guide pratique pour Afficher des erreurs d’interface utilisateur du complément](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Procédure pas à pas : Créer un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procédure pas à pas : Mettre à jour les contrôles sur un ruban lors de l’exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Procédure pas à pas : Créer un onglet personnalisé à l’aide de XML du ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
