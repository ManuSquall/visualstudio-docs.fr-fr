---
title: Concepteur de flux de travail - Concepteur d’activités State
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4d07cfeeb713767bc4f711c99b6b482759af2232
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62434072"
---
# <a name="state-activity-designer"></a>Concepteur d'activités d'état

Un <xref:System.Activities.Statements.State> représente un état dans lequel une machine à états peut être.

## <a name="using-the-state-activity-designer"></a>Utilisation du concepteur d'activités State

Pour ajouter un <xref:System.Activities.Statements.State> à un workflow, faites glisser le **état** Concepteur d’activités à partir de la **Machine à états** section de la **boîte à outils** et déposez-le sur une <xref:System.Activities.Statements.StateMachine> activité sur l’aire du Concepteur de flux de travail. Une activité <xref:System.Activities.Statements.State> peut être déposée sur un <xref:System.Activities.Statements.StateMachine> et des transitions ajoutées ultérieurement ; ou une transition peut être créée lorsque l’activité <xref:System.Activities.Statements.State> est déposée. Pour ajouter un <xref:System.Activities.Statements.State> activité et créer une transition en une seule étape, faites glisser un **état** activité à partir de la **Machine à états** section de la **boîte à outils** et placez-la sur un autre état dans le Concepteur de flux de travail. Lorsque le <xref:System.Activities.Statements.State> est déplacé vers un autre <xref:System.Activities.Statements.State>, quatre triangles apparaissent autour de l'autre <xref:System.Activities.Statements.State>. Si <xref:System.Activities.Statements.State> est déposé sur un des quatre triangles, il est ajouté à la machine à états et une transition est créée à partir du <xref:System.Activities.Statements.State> source vers le <xref:System.Activities.Statements.State> de destination de dépôt. Pour plus d’informations, consultez [Transition](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité State dans le concepteur de workflow

Le tableau suivant indique les propriétés  <xref:System.Activities.Statements.State> qui peuvent être définies à l'aide du concepteur de workflow et explique comment elles sont utilisées dans le concepteur. Certaines de ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiées dans l'aire de conception.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.State> dans l'en-tête. La valeur par défaut est **état**. La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en-tête du concepteur d'activités. <xref:System.Activities.Statements.State.DisplayName%2A> est utilisé dans l'exploration à l'aide de la barre de navigation qui est affichée en haut du concepteur de workflow.<br /><br /> Bien que la propriété <xref:System.Activities.Statements.State.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Spécifie l'action qui se produit lorsque cet état subit une transition. Lorsque le <xref:System.Activities.Statements.State> activité est développée, cette valeur peut être définie en faisant glisser une activité à partir de la **boîte à outils** et déposant sur le **entrée** section de l’état.|
|<xref:System.Activities.Statements.State.Exit%2A>|False|Spécifie l'action qui se produit lorsque cet état subit une transition. Lorsque le <xref:System.Activities.Statements.State> activité est développée, cette valeur peut être définie en faisant glisser une activité à partir de la **boîte à outils** et déposant sur le **Exit** section de l’état.|
|<xref:System.Activities.Statements.State.Transitions%2A>|False|Répertorie les transitions possibles qui proviennent de <xref:System.Activities.Statements.State>. Chaque élément de la liste inclut un lien vers le <xref:System.Activities.Statements.Transition> associé et <xref:System.Activities.Statements.State> de destination. Cliquez sur le lien pour faire basculer le concepteur dans un affichage développé de <xref:System.Activities.Statements.Transition> ou <xref:System.Activities.Statements.State>.|

## <a name="see-also"></a>Voir aussi

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)