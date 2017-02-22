---
title: "Proc&#233;dure&#160;: ajouter des activit&#233;s &#224; la bo&#238;te &#224; outils (h&#233;rit&#233;e) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "activités, ajouter à la boîte à outils"
  - "Boîte à outils, ajouter des activités"
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Proc&#233;dure&#160;: ajouter des activit&#233;s &#224; la bo&#238;te &#224; outils (h&#233;rit&#233;e)
Lors de la génération d'une solution de workflow avec le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], des activités personnalisées peuvent être ajoutées au projet de workflow et leurs concepteurs placés dans la **Boîte à outils** afin de pouvoir y accéder aisément.Vous pouvez également ajouter directement des activités à la **boîte à outils** à partir d'une bibliothèque de liens dynamiques \(DLL\).  
  
### Pour ajouter une activité à la boîte à outils à partir d'une DLL  
  
1.  Cliquez avec le bouton droit sur la surface de la fenêtre de la boîte à outils dans **Windows Workflow**, puis cliquez sur **Choisir les éléments**.  
  
2.  Dans la boîte de dialogue **Choisir des éléments de boîte à outils**, cliquez sur l'onglet **Composants System.Activities**, puis sur **Parcourir** dans l'angle inférieur droit de la fenêtre.  
  
3.  Sélectionnez la DLL du répertoire de fichiers qui contient l'implémentation de l'activité personnalisée à ajouter à la **Boîte à outils**, puis cliquez sur **Ouvrir**.  
  
4.  Cliquez sur **OK** pour terminer d'ajouter l'activité à la boîte à outils.  
  
## Voir aussi  
 [Utilisation du concepteur d'activités hérité](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Activités de workflow héritées](../workflow-designer/legacy-workflow-activities.md)