---
title: "Concepteur d&#39;activit&#233;s Pick | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Pick.UI"
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Concepteur d&#39;activit&#233;s Pick
L'activité <xref:System.Activities.Statements.Pick> fournit un flux de contrôle basé sur les événements.Elle exécute l'une des différentes branches en réponse à un événement de déclenchement.  
  
## Activité Pick  
 Une activité <xref:System.Activities.Statements.Pick> contient une collection d'objets <xref:System.Activities.Statements.PickBranch>, dont l'un peut être exécuté par l'activité <xref:System.Activities.Statements.Pick> en raison d'un événement entrant qui sert de déclencheur.De cette manière, [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] fournit la modélisation des flux de contrôle basée sur les événements.Chaque <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Trigger%2A> et une propriété <xref:System.Activities.Statements.PickBranch.Action%2A>.Au début de l'exécution d'une activité <xref:System.Activities.Statements.Pick>, toutes les activités de déclencheur des éléments <xref:System.Activities.Statements.PickBranch> sont planifiées.À l'issue de la première activité, l'activité d'action correspondante est planifiée, et toutes les autres activités de déclencheur sont annulées.  
  
### Comment utiliser le concepteur d'activités Pick  
 Le concepteur d'activités **Pick** se trouve dans la catégorie **Flux de contrôle** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **Pick** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les concepteurs d'activités sont généralement placés, par exemple dans un concepteur d'activités **Sequence**.Une fois déposé dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], il crée une activité <xref:System.Activities.Statements.Pick>, laquelle contient par défaut deux activités <xref:System.Activities.Statements.PickBranch> vides comme éléments ayant les noms complets Branch1 et Branch2.Ces valeurs de propriétés <xref:System.Activities.Statements.PickBranch.DisplayName%2A> respectives peuvent être modifiées dans l'en\-tête du concepteur d'activités **PickBranch** ou dans la fenêtre **Propriétés** pour chaque branche.  
  
 Il existe deux façons d'ajouter des activités <xref:System.Activities.Statements.PickBranch> à la collection d'un objet <xref:System.Activities.Statements.Pick> : en déplaçant le concepteur **PickBranch** à partir de la **Boîte à outils** ou en utilisant le menu contextuel à partir de l'aire de conception **Pick**.Pour plus d'informations, consultez la rubrique [PickBranch](../workflow-designer/pickbranch-activity-designer.md).Notez que le seul élément qui peut être placé à l'intérieur d'un concepteur d'activités **Pick** est un concepteur d'activités **PickBranch**.  
  
### Propriétés de l'activité Pick dans le concepteur de workflow  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Pick> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire de conception.  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.Pick> dans l'en\-tête.La valeur par défaut est Pick.La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en\-tête du concepteur d'activités.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
  
## Voir aussi  
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)   
 [Activité Pick](../Topic/Pick%20Activity.md)   
 [Utilisation de l'activité Pick](../Topic/Using%20the%20Pick%20Activity.md)