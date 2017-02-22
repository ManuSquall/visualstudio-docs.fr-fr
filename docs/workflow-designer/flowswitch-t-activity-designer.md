---
title: "Concepteur d&#39;activit&#233;s FlowSwitch&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Core.Presentation.FlowSwitchLink.UI"
  - "System.Activities.Statements.FlowSwitch`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLink`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI"
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Concepteur d&#39;activit&#233;s FlowSwitch&lt;T&gt;
L'activité <xref:System.Activities.Statements.FlowSwitch%601> est un nœud conditionnel qui fournit la création de branches pour le flux de contrôle selon un critère de correspondance lorsque plus de deux branches sont requises.Si la création de branches de flux requiert uniquement deux chemins d'accès, utilisez l'activité <xref:System.Activities.Statements.FlowDecision> à la place.  
  
## Activité FlowSwitch\<T\>  
 L'activité <xref:System.Activities.Statements.FlowSwitch%601> contient une propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> qui retourne une valeur de type *T* \(spécifiée par le paramètre générique\) lorsqu'elle est évaluée.L'activité contient également un jeu de propriétés <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, qui spécifie un mappage unique, à partir des résultats possibles de cette évaluation, à un jeu d'objets <xref:System.Activities.Statements.FlowNode>.L'objet <xref:System.Activities.Statements.FlowNode> exécuté est celui dont l'objet de type *T* correspond à la valeur de la propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> évaluée.Un cas <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> peut être fourni \(éventuellement\) pour le cas dans lequel aucune correspondance n'est obtenue.  
  
### Utilisation du concepteur d'activités FlowSwitch\<T\>  
 Le concepteur d'activités **FlowSwitch\<T\>** se trouve dans la catégorie **Organigramme** de la **boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** à gauche de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 Le concepteur d'activités **FlowSwitch\<T\>** peut être déplacé de la **boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] dans un concepteur d'activités **Flowchart**.Utilisez la fenêtre **Sélectionner les types** qui s'affiche pour spécifier le type \(associé dans le code à <xref:System.Activities.Statements.FlowSwitch%601> par son paramètre générique\) obtenu de l'évaluation de la propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>.Cette procédure crée une activité <xref:System.Activities.Statements.FlowSwitch%601> étiquetée **Switch** dans l'activité <xref:System.Activities.Statements.Flowchart>.Vous pouvez taper la propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> dans la zone **Expression** de la fenêtre **Propriétés** en cliquant à l'endroit où le texte d'indication « Entrer une expression VB » apparaît.  
  
 Pointez avec la souris sur le concepteur d'activités **FlowSwitch\<T\>** pour faire apparaître sur ses bords les poignées carrées utilisées pour lier la propriété <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.Après avoir fait glisser le concepteur d'activités **FlowSwitch\<T\>** et les autres concepteurs d'activités sur l'**organigramme**, les objets <xref:System.Activities.Activity> qu'ils représentent sont prêts à être liés pour spécifier l'ordre d'exécution.Pour créer une des propriétés <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> associées à <xref:System.Activities.Statements.FlowSwitch%601>, cliquez sur l'une des poignées de cas carrées situées sur le périmètre du **FlowSwitch\<T\>** et faites\-la glisser \(en maintenant le bouton de la souris enfoncé\) vers l'une des poignées qui s'affichent de façon semblable autour de l'activité de destination lorsque la souris pointe sur son concepteur.Lorsque vous relâchez le bouton de la souris, une flèche représentant ce cas apparaît entre **FlowSwitch\<T\>** et le concepteur de destination.La valeur par défaut de ce cas s'affiche sur la flèche. Elle peut être modifiée dans la zone **Cas** de la fenêtre **Propriétés**.  
  
### Propriétés FlowSwitch\<T\>  
 Le tableau suivant présente les propriétés <xref:System.Activities.Statements.FlowSwitch%601> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------------|-----------------|-----------------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Spécifie l'expression qui est évaluée pour déterminer le cas du jeu de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> vers lequel basculer dans le chemin d'exécution.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Spécifie un mappage unique, à partir des résultats possibles obtenus de l'évaluation de la propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, à un jeu d'objets <xref:System.Activities.Statements.FlowNode>.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Spécifie le mappage lorsque l'évaluation de la propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> ne correspond pas à l'une des valeurs contenues dans l'objet <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|  
  
## Voir aussi  
 [Organigramme](../workflow-designer/flowchart-activity-designers.md)   
 [Organigramme](../workflow-designer/flowchart-activity-designer.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)