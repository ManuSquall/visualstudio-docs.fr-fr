---
title: Concepteur de flux de travail - FlowSwitch<T> Concepteur d’activités
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3f6d396acb62b9cac8f34ef106ac96257eec612
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970844"
---
# <a name="flowswitcht-activity-designer"></a>FlowSwitch\<T > Concepteur d’activités

L’activité <xref:System.Activities.Statements.FlowSwitch%601> est un nœud conditionnel qui fournit la création de branches pour le flux de contrôle selon un critère de correspondance lorsque plus de deux branches sont requises. Si la création de branches de flux requiert uniquement deux chemins d’accès, utilisez l’activité <xref:System.Activities.Statements.FlowDecision> à la place.

## <a name="the-flowswitcht-activity"></a>FlowSwitch\<T > activité

Le <xref:System.Activities.Statements.FlowSwitch%601> activité contient un <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> qui retourne une valeur de type *T* (spécifié par le paramètre générique) lors de l’évaluation. L'activité contient également un jeu de propriétés <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, qui spécifie un mappage unique, à partir des résultats possibles de cette évaluation, à un jeu d'objets <xref:System.Activities.Statements.FlowNode>. Le <xref:System.Activities.Statements.FlowNode> exécuté est celui dont l’objet de type *T* correspond à la valeur de la liste évaluée <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Un cas <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> peut être fourni (éventuellement) pour le cas dans lequel aucune correspondance n'est obtenue.

### <a name="using-the-flowswitcht-activity-designer"></a>À l’aide de FlowSwitch\<T > Concepteur d’activités

Le **FlowSwitch\<T >** Concepteur d’activités peut être trouvé dans le **organigramme** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **Boîte à outils** onglet sur le côté gauche du Concepteur de Workflow. Vous pouvez également sélectionner **boîte à outils** à partir de la **vue** menu, ou appuyez sur **Ctrl**+**Alt** + **X**.

Le **FlowSwitch\<T >** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail au sein d’un **organigramme** Concepteur d’activités. Utilisez le **sélectionner les Types** fenêtre qui s’affiche pour spécifier le type (associé dans le code avec le <xref:System.Activities.Statements.FlowSwitch%601> par son paramètre générique) obtenu à partir de l’évaluation de la <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Cette procédure crée un <xref:System.Activities.Statements.FlowSwitch%601> activité intitulée **commutateur** au sein de la <xref:System.Activities.Statements.Flowchart> activité. Le <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> peuvent être tapés dans le **Expression** boîte de le **propriétés** fenêtre en cliquant sur où le texte d’indication est « Entrer une expression VB ».

Placez la souris sur le **FlowSwitch\<T >** Concepteur d’activités pour provoquer des poignées carrées utilisées pour la liaison <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> à apparaître sur ses bords. Après avoir fait glisser le **FlowSwitch < T\>**  Concepteur d’activités et d’autres concepteurs d’activités sur le **organigramme**, le <xref:System.Activities.Activity> objets qu’ils représentent sont prêts à être liées Pour spécifier l’ordre d’exécution. Pour créer un de la <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> associé à la <xref:System.Activities.Statements.FlowSwitch%601>, cliquez sur une des poignées de cas carrées sur le périmètre de la **FlowSwitch < T\>**  et faites-la glisser (en maintenant enfoncé le bouton de la souris) à une des poignées qui apparaît de façon semblable autour de l’activité de destination lorsque la souris pointe sur son concepteur. Relâchez le bouton de la souris, une flèche à partir de la **FlowSwitch < T\>**  au Concepteur de destination s’affiche représentant ce cas. La valeur par défaut pour ce cas s’affiche sur la flèche et il peut être modifié dans le **cas** zone de la **propriétés** fenêtre.

### <a name="the-flowswitcht-properties"></a>FlowSwitch\<T > Propriétés

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.FlowSwitch%601> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Spécifie l'expression qui est évaluée pour déterminer le cas du jeu de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> vers lequel basculer dans le chemin d'exécution.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Spécifie un mappage unique, à partir des résultats possibles obtenus de l'évaluation de la propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, à un jeu d'objets <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Spécifie le mappage lorsque l'évaluation de la propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> ne correspond pas à l'une des valeurs contenues dans l'objet <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Voir aussi

- [Organigramme](../workflow-designer/flowchart-activity-designers.md)
- [Organigramme](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)