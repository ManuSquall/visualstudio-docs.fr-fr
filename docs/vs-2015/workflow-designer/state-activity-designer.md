---
title: Concepteur d’activités d’État | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2c1eea76a2593f4c0de817b8439361bd1be37b5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663193"
---
# <a name="state-activity-designer"></a>Concepteur d'activités d'état
Un <xref:System.Activities.Statements.State> représente un état dans lequel une machine à états peut être.

## <a name="using-the-state-activity-designer"></a>Utilisation du concepteur d'activités State
 Pour ajouter un <xref:System.Activities.Statements.State> à un workflow, faites glisser le concepteur d’activités **State** de la section **machine à États** de la **boîte à outils** et déposez-le sur une <xref:System.Activities.Statements.StateMachine> activité sur l' [!INCLUDE[wfd1](../includes/wfd1-md.md)] aire de conception. Une activité <xref:System.Activities.Statements.State> peut être déposée sur un <xref:System.Activities.Statements.StateMachine> et des transitions ajoutées ultérieurement ; ou une transition peut être créée lorsque l’activité <xref:System.Activities.Statements.State> est déposée. Pour ajouter une <xref:System.Activities.Statements.State> activité et créer une transition en une seule étape, faites glisser une activité **State** de la section **machine à États** de la **boîte à outils** et placez-la sur un autre État dans le concepteur de Workflow. Lorsque le <xref:System.Activities.Statements.State> est déplacé vers un autre <xref:System.Activities.Statements.State>, quatre triangles apparaissent autour de l'autre <xref:System.Activities.Statements.State>. Si <xref:System.Activities.Statements.State> est déposé sur un des quatre triangles, il est ajouté à la machine à états et une transition est créée à partir du <xref:System.Activities.Statements.State> source vers le <xref:System.Activities.Statements.State> de destination de dépôt. Pour plus d’informations, consultez [transition](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité State dans le concepteur de workflow
 Le tableau suivant indique les propriétés  <xref:System.Activities.Statements.State> qui peuvent être définies à l'aide du concepteur de workflow et explique comment elles sont utilisées dans le concepteur. Certaines de ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiées dans l'aire de conception.

|Nom de la propriété|Obligatoire|Usage|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Faux|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.State> dans l'en-tête. La valeur par défaut est **State**. La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en-tête du concepteur d'activités. <xref:System.Activities.Statements.State.DisplayName%2A> est utilisé dans l'exploration à l'aide de la barre de navigation qui est affichée en haut du concepteur de workflow.<br /><br /> Bien que la propriété <xref:System.Activities.Statements.State.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.State.Entry%2A>|Faux|Spécifie l'action qui se produit lorsque cet état subit une transition. Lorsque l' <xref:System.Activities.Statements.State> activité est développée, cette valeur peut être définie en faisant glisser une activité de la **boîte à outils** et en la déposant sur la section d' **entrée** de l’État.|
|<xref:System.Activities.Statements.State.Exit%2A>|Faux|Spécifie l'action qui se produit lorsque cet état subit une transition. Lorsque l' <xref:System.Activities.Statements.State> activité est développée, cette valeur peut être définie en faisant glisser une activité de la **boîte à outils** et en la déposant sur la section **Exit** de l’État.|
|<xref:System.Activities.Statements.State.Transitions%2A>|Faux|Répertorie les transitions possibles qui proviennent de <xref:System.Activities.Statements.State>. Chaque élément de la liste inclut un lien vers le <xref:System.Activities.Statements.Transition> associé et <xref:System.Activities.Statements.State> de destination. Cliquez sur le lien pour faire basculer le concepteur dans un affichage développé de <xref:System.Activities.Statements.Transition> ou <xref:System.Activities.Statements.State>.|

## <a name="see-also"></a>Voir aussi
 [StateMachine](../workflow-designer/statemachine-activity-designer.md) [FinalState](../workflow-designer/finalstate-activity-designer.md) [Transition](../workflow-designer/transition-activity-designer.md) FinalState StateMachine