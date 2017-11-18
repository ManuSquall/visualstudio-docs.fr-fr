---
title: "Comment : ajouter des activités à la boîte à outils (hérité) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9b0dce8c2600d125a84044bef60957bd1bfa8b44
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Procédure : ajouter des activités à la boîte à outils (héritée)
Lors de la création d’une solution de workflow avec hérité [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], des activités personnalisées peuvent être ajoutées au projet de workflow et leurs concepteurs placés dans le **boîte à outils** pour facile accès. Vous pouvez également ajouter des activités directement à la **boîte à outils** à partir d’une bibliothèque de liens dynamiques (DLL).  
  
### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Pour ajouter une activité à la boîte à outils à partir d'une DLL  
  
1.  Avec le bouton droit de la surface de la fenêtre Boîte à outils sous **Windows Workflow**, puis cliquez sur **choisir des éléments de**.  
  
2.  Dans le **choisir des éléments de boîte à outils** boîte de dialogue, cliquez sur le **System.Activities Components** onglet, puis cliquez sur **Parcourir** à partir de l’angle inférieur droit de la fenêtre.  
  
3.  Sélectionnez la DLL dans le répertoire de fichier qui contient l’implémentation de l’activité personnalisée à ajouter à la **boîte à outils**, puis cliquez sur **ouvrir**.  
  
4.  Cliquez sur **OK** pour terminer l’ajout de l’activité à la boîte à outils.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide du Concepteur d’activités hérité](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)