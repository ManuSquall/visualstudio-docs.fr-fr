---
title: "Comment : ajouter un lanceur de boîte de dialogue à un groupe de ruban | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 49dee3d090e2b7f985fd85a6061dea3a2c204e4a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Comment : ajouter un lanceur de boîte de dialogue à un groupe de ruban
  Vous pouvez ajouter un lanceur de boîte de dialogue à un groupe sur un ruban. Un lanceur de boîte de dialogue est une petite icône qui apparaît dans un groupe. Les utilisateurs cliquent sur cette icône pour ouvrir des boîtes de dialogue connexes ou des volets de tâches qui fournissent des options supplémentaires qui se rapportent au groupe.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Pour ajouter un lanceur de boîte de dialogue à un groupe de ruban  
  
1.  Sélectionnez le fichier de code du ruban (fichier .vb ou .cs) dans **l’Explorateur de solutions**.  
  
2.  Sur le **vue** menu, cliquez sur **concepteur**.  
  
3.  Dans le Concepteur de ruban, avec le bouton droit n’importe quel groupe, puis cliquez sur **Ajouter DialogBoxLauncher**.  
  
     Ajoutez le code pour le <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> événement du groupe pour ouvrir une boîte de dialogue personnalisée ou intégrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Procédures pas à pas et des exemples de développement office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Présentation du modèle objet de ruban](../vsto/ribbon-object-model-overview.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Comment : exporter un ruban à partir du Concepteur de ruban vers ruban XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Comment : modifier la Position d’un onglet du ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)   
 [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Personnalisation d’un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Comment : afficher les erreurs d’Interface utilisateur du complément](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Procédure pas à pas : Création d’un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procédure pas à pas : Mise à jour les contrôles sur un ruban au moment de l’exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Procédure pas à pas : création d’un onglet personnalisé à l’aide d’un élément XML Ribbon](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  