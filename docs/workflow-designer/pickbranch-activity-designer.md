---
title: "Concepteur d&#39;activit&#233;s PickBranch | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.PickBranch.UI"
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Concepteur d&#39;activit&#233;s PickBranch
L'objet <xref:System.Activities.Statements.PickBranch> fournit un chemin d'accès d'exécution basé sur les événements dans une activité <xref:System.Activities.Statements.Pick> qui peut être déclenchée par un événement entrant.  
  
## PickBranch  
 Les objets <xref:System.Activities.Statements.PickBranch> sont contenus dans la collection <xref:System.Activities.Statements.Pick.Branches%2A> d'une activité <xref:System.Activities.Statements.Pick>.Chaque <xref:System.Activities.Statements.PickBranch> est contenue dans une branche de l'activité <xref:System.Activities.Statements.Pick> et peut être exécutée en raison d'un événement entrant qui sert de déclencheur.De cette manière, [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] fournit la modélisation des flux de contrôle basée sur les événements.Chaque <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Trigger%2A> et une propriété <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### Comment utiliser le concepteur d'activités Pick  
 Le concepteur **PickBranch** se trouve dans la catégorie **Flux de contrôle** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Deux objets <xref:System.Activities.Statements.PickBranch> vides ayant les noms complets **Branch1** et **Branch2** sont créés par défaut comme éléments d'une activité <xref:System.Activities.Statements.Pick> lorsque le concepteur d'activités **Pick** est initialement déposé sur le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Ces valeurs de propriétés <xref:System.Activities.Statements.PickBranch.DisplayName%2A> respectives peuvent être modifiées dans l'en\-tête du concepteur **PickBranch** ou dans la fenêtre **Propriétés** pour chaque branche.  
  
 Il existe deux façons d'ajouter des objets <xref:System.Activities.Statements.PickBranch> à la collection d'un objet <xref:System.Activities.Statements.Pick> : en déplaçant le concepteur **PickBranch** à partir de la **Boîte à outils** ou en utilisant le menu contextuel à partir de l'aire de conception **Pick** :  
  
1.  Le concepteur **PickBranch** crée un objet <xref:System.Activities.Statements.PickBranch> lorsqu'il est déplacé depuis la **Boîte à outils** et déposé dans l'une des branches d'un concepteur d'activités **Pick** sur l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Les nouveaux objets <xref:System.Activities.Statements.PickBranch> peuvent être placés dans le concepteur <xref:System.Activities.Statements.Pick> à gauche ou à droite des éléments <xref:System.Activities.Statements.PickBranch> existants déjà contenus dans la collection.Lors du déplacement d'un concepteur **PickBranch** sur le concepteur **Pick** avec une souris, le concepteur **Pick** utilise une bande bleu gris verticale pour indiquer l'endroit où l'objet <xref:System.Activities.Statements.PickBranch> est ajouté pour un positionnement de souris donné.  
  
2.  Cliquez avec le bouton droit sur le concepteur d'activités **Pick** \(mais pas à l'intérieur du concepteur **PickBranch**\) pour afficher un menu contextuel et sélectionnez **Créer une branche** pour ajouter un nouveau <xref:System.Activities.Statements.PickBranch>.Notez que le nouvel objet <xref:System.Activities.Statements.PickBranch> est ajouté à droite des objets <xref:System.Activities.Statements.PickBranch> existants dans le concepteur **Pick**.  
  
 Le concepteur **PickBranch** peut être développé pour révéler les zones **Déclencheur** et **Action** ou réduit en cliquant sur le double signe ^ à droite de leurs en\-têtes.Modifiez les propriétés <xref:System.Activities.Statements.PickBranch.Trigger%2A> et <xref:System.Activities.Statements.PickBranch.Action%2A> de chaque objet <xref:System.Activities.Statements.PickBranch> en déposant des activités dans les zones **Déclencheur** et **Action** de leurs concepteurs.  
  
 Vous pouvez réorganiser les objets <xref:System.Activities.Statements.PickBranch> de la collection <xref:System.Activities.Statements.Pick.Branches%2A> d'un objet <xref:System.Activities.Statements.Pick> en les faisant glisser et en les déposant à un nouvel emplacement dans le concepteur **Pick**.Le concepteur **Pick** utilise une bande bleu gris verticale pour indiquer l'endroit où l'objet <xref:System.Activities.Statements.PickBranch> est ajouté pour un positionnement de souris donné.  
  
 Il existe deux façons de supprimer un objet <xref:System.Activities.Statements.PickBranch> :  
  
1.  Sélectionnez le concepteur **PickBranch** et supprimez\-le.  
  
2.  Sélectionnez le concepteur **PickBranch**, cliquez avec le bouton droit pour afficher le menu contextuel, puis sélectionnez **Supprimer**.  
  
 Veillez à sélectionner le concepteur **PickBranch**, car la sélection accidentelle de l'une des activités à l'intérieur de ses zones **Déclencheur** ou **Action** supprime l'une de ces activités, et non pas l'objet <xref:System.Activities.Statements.PickBranch>.  
  
### Propriétés de PickBranch dans le concepteur de workflow  
 Le tableau suivant affiche les propriétés les plus utiles de <xref:System.Activities.Statements.PickBranch> et décrit comment les utiliser dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Nom convivial affiché dans l'en\-tête du concepteur **PickBranch**.La valeur par défaut est Branch.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Chaque objet <xref:System.Activities.Statements.PickBranch> contient une action <xref:System.Activities.Statements.PickBranch.Trigger%2A> qui peut appeler la propriété <xref:System.Activities.Statements.PickBranch.Action%2A>.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Chaque objet <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Action%2A> qui est exécutée en cas de déclenchement.|  
  
## Voir aussi  
 [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)   
 [Activité Pick](../Topic/Pick%20Activity.md)   
 [Utilisation de l'activité Pick](../Topic/Using%20the%20Pick%20Activity.md)