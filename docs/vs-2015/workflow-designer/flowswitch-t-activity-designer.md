---
title: Concepteur d’activités FlowSwitch &lt;T &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 27abb660766a7c04742eca221432af19f05f0d28
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656646"
---
# <a name="flowswitchlttgt-activity-designer"></a>Concepteur d’activités FlowSwitch &lt;T &gt;
L’activité <xref:System.Activities.Statements.FlowSwitch%601> est un nœud conditionnel qui fournit la création de branches pour le flux de contrôle selon un critère de correspondance lorsque plus de deux branches sont requises. Si la création de branches de flux requiert uniquement deux chemins d’accès, utilisez l’activité <xref:System.Activities.Statements.FlowDecision> à la place.

## <a name="the-flowswitcht-activity"></a>Activité FlowSwitch \<T >
 L’activité <xref:System.Activities.Statements.FlowSwitch%601> contient une <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> qui retourne une valeur de type *t* (spécifiée par le paramètre générique) lors de l’évaluation. L'activité contient également un jeu de propriétés <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, qui spécifie un mappage unique, à partir des résultats possibles de cette évaluation, à un jeu d'objets <xref:System.Activities.Statements.FlowNode>. Le <xref:System.Activities.Statements.FlowNode> exécuté est celui dont l’objet de type *t* correspond à la valeur du <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> évalué. Un cas <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> peut être fourni (éventuellement) pour le cas dans lequel aucune correspondance n'est obtenue.

### <a name="using-the-flowswitcht-activity-designer"></a>Utilisation du concepteur d’activités FlowSwitch \<T >
 Le concepteur d’activités **FlowSwitch \<T >** se trouve dans la catégorie **organigramme** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** sur le côté gauche du [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans le menu **affichage** , ou CTRL + ALT + X.)

 Le concepteur d’activités **FlowSwitch \<T >** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)] dans un concepteur d’activités **Flowchart** . Utilisez la fenêtre **Sélectionner les types** qui s’affiche pour spécifier le type (associé au code avec le <xref:System.Activities.Statements.FlowSwitch%601> par son paramètre générique) obtenu à partir de l’évaluation de l' <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Cette procédure crée une activité <xref:System.Activities.Statements.FlowSwitch%601> appelée **switch** dans l’activité <xref:System.Activities.Statements.Flowchart>. La <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> peut être tapée dans la zone **expression** de la fenêtre **Propriétés** en cliquant à l’endroit où le texte d’indication indique « entrer une expression VB ».

 Placez la souris sur **FlowSwitch \<T >** concepteur d’activités pour faire apparaître les poignées carrées utilisées pour lier les <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> à des bords. Après avoir fait glisser le concepteur d’activités **FlowSwitch < T \>** et d’autres concepteurs d’activités dans l' **organigramme**, les objets <xref:System.Activities.Activity> qu’ils représentent sont prêts à être liés pour spécifier l’ordre d’exécution. Pour créer l’un des <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> associés à l' <xref:System.Activities.Statements.FlowSwitch%601>, cliquez sur l’une des poignées de case carrées sur le périmètre du **FlowSwitch \<T >** et faites-la glisser (en maintenant enfoncé le bouton de la souris) sur l’une des poignées qui s’affichent de la même manière dans le activité de destination lorsque la souris pointe sur son concepteur. Relâchez le bouton de la souris et une flèche à partir du **\<T FlowSwitch >** dans le concepteur de destination apparaît et représente ce cas. La valeur par défaut de ce cas s’affiche sur la flèche et peut être modifiée dans **la zone case de la fenêtre** **Propriétés** .

### <a name="the-flowswitcht-properties"></a>Propriétés du > \<T FlowSwitch
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.FlowSwitch%601> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Spécifie l’expression qui est évaluée pour déterminer le cas du jeu de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> vers lequel basculer dans le chemin d’exécution.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Spécifie un mappage unique, à partir des résultats possibles obtenus de l'évaluation de la propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, à un jeu d'objets <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Spécifie le mappage lorsque l'évaluation de la propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> ne correspond pas à l'une des valeurs contenues dans l'objet <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Voir aussi
 [Organigramme](../workflow-designer/flowchart-activity-designers.md) [Organigramme](../workflow-designer/flowchart-activity-designer.md) [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)