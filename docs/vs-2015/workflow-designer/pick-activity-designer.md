---
title: Concepteur d’activités Pick | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: d5bf361d2217c199fa2818a94c441e1d2b105e7f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494192"
---
# <a name="pick-activity-designer"></a>Concepteur d'activités Pick
L'activité <xref:System.Activities.Statements.Pick> fournit un flux de contrôle basé sur les événements. Elle exécute l'une des différentes branches en réponse à un événement de déclenchement.  
  
## <a name="the-pick-activity"></a>Activité Pick  
 Une activité <xref:System.Activities.Statements.Pick> contient une collection d'objets <xref:System.Activities.Statements.PickBranch>, dont l'un peut être exécuté par l'activité <xref:System.Activities.Statements.Pick> en raison d'un événement entrant qui sert de déclencheur. De cette manière, [!INCLUDE[wfd1](../includes/wfd1-md.md)] fournit la modélisation des flux de contrôle basée sur les événements. Chaque <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Trigger%2A> et une propriété <xref:System.Activities.Statements.PickBranch.Action%2A>. Au début de l'exécution d'une activité <xref:System.Activities.Statements.Pick>, toutes les activités de déclencheur des éléments <xref:System.Activities.Statements.PickBranch> sont planifiées. À l'issue de la première activité, l'activité d'action correspondante est planifiée et toutes les autres activités de déclencheur sont annulées.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Comment utiliser le concepteur d'activités Pick  
 Le **choisir** Concepteur d’activités peut être trouvé dans le **flux de contrôle** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils**onglet [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)  
  
 Le **choisir** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface, là où concepteurs d’activités sont généralement placés, par exemple à l’intérieur d’un  **Séquence** Concepteur d’activités. Une fois déposé dans [!INCLUDE[wfd2](../includes/wfd2-md.md)], il crée une activité <xref:System.Activities.Statements.Pick>, laquelle contient par défaut deux activités <xref:System.Activities.Statements.PickBranch> vides comme éléments ayant les noms complets Branch1 et Branch2. Ces respectifs <xref:System.Activities.Statements.PickBranch.DisplayName%2A> les valeurs de propriété peuvent être modifiées dans le **PickBranch** en-tête du Concepteur d’activité ou à l’intérieur du **propriétés** fenêtre pour chaque branche.  
  
 Il existe deux façons d’ajouter <xref:System.Activities.Statements.PickBranch> activités à la collection d’un <xref:System.Activities.Statements.Pick> objet : glisser- déposer le **PickBranch** concepteur à partir de la **boîte à outils** ou en utilisant le menu contextuel à partir de dans le **choisir** aire de conception. Pour plus d’informations, consultez le [PickBranch](../workflow-designer/pickbranch-activity-designer.md) rubrique. Notez que le seul élément qui peut être placé à l’intérieur d’un **choisir** Concepteur d’activités est un **PickBranch** Concepteur d’activités.  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité Pick dans le concepteur de workflow  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Pick> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.Pick> dans l'en-tête. La valeur par défaut est Pick. La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en-tête du concepteur d'activités.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)   
 [Activité Pick](http://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [Utilisation de l’activité Pick](http://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)