---
title: 'Comment : ajouter des activités à la boîte à outils (hérité) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 0fafcc260f451c4ead24d7a9dbb72a4db22c0b79
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249364"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Procédure : ajouter des activités à la boîte à outils (héritée)
Lors de la création d’une solution de flux de travail avec les anciennes [!INCLUDE[wfd1](../includes/wfd1-md.md)] qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], activités personnalisées peuvent être ajoutées au projet de workflow et leurs concepteurs placés dans le **boîte à outils** pour facile accès. Vous pouvez également ajouter des activités directement à la **boîte à outils** à partir d’une bibliothèque de liens dynamiques (DLL).  
  
### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Pour ajouter une activité à la boîte à outils à partir d'une DLL  
  
1.  Avec le bouton droit de la surface de la fenêtre Boîte à outils sous **Windows Workflow**, puis cliquez sur **choisir des éléments de**.  
  
2.  Dans le **Choose Toolbox Items** boîte de dialogue, cliquez sur le **composants System.Activities** onglet, puis cliquez sur **Parcourir** à partir de l’angle inférieur droit de la fenêtre.  
  
3.  Sélectionnez la DLL dans le répertoire de fichier qui contient l’implémentation de l’activité personnalisée à ajouter à la **boîte à outils**, puis cliquez sur **Open**.  
  
4.  Cliquez sur **OK** pour terminer l’ajout de l’activité à la boîte à outils.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide du Concepteur d’activités hérité](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)