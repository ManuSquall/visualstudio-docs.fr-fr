---
title: 'Procédure : Ajouter des activités à la boîte à outils (hérité) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 51c9d43a1dee05d1b1cb77e50aa2d54d4f4e7f2c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951234"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Procédure : Ajouter des activités à la boîte à outils (héritées)
Lors de la création d’une solution de flux de travail avec les anciennes [!INCLUDE[wfd1](../includes/wfd1-md.md)] qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], activités personnalisées peuvent être ajoutées au projet de workflow et leurs concepteurs placés dans le **boîte à outils** pour facile accès. Vous pouvez également ajouter des activités directement à la **boîte à outils** à partir d’une bibliothèque de liens dynamiques (DLL).  
  
### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Pour ajouter une activité à la boîte à outils à partir d'une DLL  
  
1.  Avec le bouton droit de la surface de la fenêtre Boîte à outils sous **Windows Workflow**, puis cliquez sur **choisir des éléments de**.  
  
2.  Dans le **Choose Toolbox Items** boîte de dialogue, cliquez sur le **composants System.Activities** onglet, puis cliquez sur **Parcourir** à partir de l’angle inférieur droit de la fenêtre.  
  
3.  Sélectionnez la DLL dans le répertoire de fichier qui contient l’implémentation de l’activité personnalisée à ajouter à la **boîte à outils**, puis cliquez sur **Open**.  
  
4.  Cliquez sur **OK** pour terminer l’ajout de l’activité à la boîte à outils.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide du Concepteur d’activités hérité](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)