---
title: "Concepteur d’activités Pick | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: "9"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: aa06d4c63dbb18c080c8a6b8ffda01838607ba55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="pick-activity-designer"></a>Concepteur d'activités Pick
L'activité <xref:System.Activities.Statements.Pick> fournit un flux de contrôle basé sur les événements. Elle exécute l'une des différentes branches en réponse à un événement de déclenchement.  
  
## <a name="the-pick-activity"></a>Activité Pick  
 Une activité <xref:System.Activities.Statements.Pick> contient une collection d'objets <xref:System.Activities.Statements.PickBranch>, dont l'un peut être exécuté par l'activité <xref:System.Activities.Statements.Pick> en raison d'un événement entrant qui sert de déclencheur. De cette manière, [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] fournit la modélisation des flux de contrôle basée sur les événements. Chaque <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Trigger%2A> et une propriété <xref:System.Activities.Statements.PickBranch.Action%2A>. Au début d’un <xref:System.Activities.Statements.Pick> l’exécution d’activité, toutes les activités de déclencheur de la <xref:System.Activities.Statements.PickBranch> éléments sont planifiées. À l'issue de la première activité, l'activité d'action correspondante est planifiée et toutes les autres activités de déclencheur sont annulées.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Comment utiliser le concepteur d'activités Pick  
 Le **choisir** Concepteur d’activités peut être trouvé dans le **flux de contrôle** catégorie de la **boîte à outils**, qui est accessible en cliquant sur les **boîte à outils**onglet [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)  
  
 Le **choisir** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] surface, là où les concepteurs d’activités sont généralement placés, par exemple à l’intérieur d’un  **Séquence** Concepteur d’activités. Une fois déposé dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], il crée une activité <xref:System.Activities.Statements.Pick>, laquelle contient par défaut deux activités <xref:System.Activities.Statements.PickBranch> vides comme éléments ayant les noms complets Branch1 et Branch2. Ces respectifs <xref:System.Activities.Statements.PickBranch.DisplayName%2A> les valeurs de propriété peuvent être modifiées dans le **PickBranch** en-tête du Concepteur d’activité ou à l’intérieur du **propriétés** fenêtre pour chaque branche.  
  
 Il existe deux façons d’ajouter <xref:System.Activities.Statements.PickBranch> activités à la collection d’un <xref:System.Activities.Statements.Pick> objet : glisser- déposer le **PickBranch** concepteur à partir de la **boîte à outils** ou à l’aide du menu contextuel dans dans le **choisir** aire de conception. Pour plus d’informations, consultez la [PickBranch](../workflow-designer/pickbranch-activity-designer.md) rubrique. Notez que le seul élément qui peut être placé à l’intérieur d’un **choisir** Concepteur d’activités est un **PickBranch** Concepteur d’activités.  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité Pick dans le concepteur de workflow  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Pick> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.Pick> dans l'en-tête. La valeur par défaut est Pick. La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en-tête du concepteur d'activités.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)   
 [Activité Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)   
 [À l’aide de l’activité Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)