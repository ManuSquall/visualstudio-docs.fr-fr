---
title: Concepteur d’activités Concepteur de flux de travail-FlowSwitch &lt; T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6637682bd6ba649f27c1a53f3b1448629f03736
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88711571"
---
# <a name="flowswitcht-activity-designer"></a>Concepteur d’activités FlowSwitch\<T>

L’activité <xref:System.Activities.Statements.FlowSwitch%601> est un nœud conditionnel qui fournit la création de branches pour le flux de contrôle selon un critère de correspondance lorsque plus de deux branches sont requises. Si la création de branches de flux requiert uniquement deux chemins d’accès, utilisez l’activité <xref:System.Activities.Statements.FlowDecision> à la place.

## <a name="the-flowswitcht-activity"></a>Activité FlowSwitch \<T>

L' <xref:System.Activities.Statements.FlowSwitch%601> activité contient un <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> qui retourne une valeur de type *T* (spécifiée par le paramètre générique) lors de l’évaluation. L'activité contient également un jeu de propriétés <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, qui spécifie un mappage unique, à partir des résultats possibles de cette évaluation, à un jeu d'objets <xref:System.Activities.Statements.FlowNode>. Le <xref:System.Activities.Statements.FlowNode> exécuté est celui dont l’objet de type *T* correspond à la valeur de l’objet évalué <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Un cas <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> peut être fourni (éventuellement) pour le cas dans lequel aucune correspondance n'est obtenue.

### <a name="using-the-flowswitcht-activity-designer"></a>Utilisation du \<T> Concepteur d’activités FlowSwitch

Le concepteur d’activités **FlowSwitch \<T> ** se trouve dans la catégorie **organigramme** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** sur le côté gauche de la concepteur de flux de travail. Vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL** + **ALT** + **X**.

Le concepteur d’activités **FlowSwitch \<T> ** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail dans un concepteur d’activités **Flowchart** . Utilisez la fenêtre **Sélectionner les types** qui s’affiche pour spécifier le type (associé au code avec le <xref:System.Activities.Statements.FlowSwitch%601> par son paramètre générique) obtenu à partir de l’évaluation de <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> . Cette procédure crée une <xref:System.Activities.Statements.FlowSwitch%601> activité nommée **switch** dans l' <xref:System.Activities.Statements.Flowchart> activité. Le <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> peut être tapé dans la zone **expression** de la fenêtre **Propriétés** en cliquant sur l’emplacement où le texte d’indication indique « entrer une expression VB ».

Placez la souris sur le concepteur d’activités **FlowSwitch \<T> ** pour faire apparaître les poignées carrées utilisées pour établir une liaison <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> avec ses bords. Après avoir fait glisser le concepteur d’activités **FlowSwitch<T \> ** et les autres concepteurs d’activités dans l' **organigramme**, les <xref:System.Activities.Activity> objets qu’ils représentent sont prêts à être liés pour spécifier l’ordre d’exécution. Pour créer l’un des <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> associés au <xref:System.Activities.Statements.FlowSwitch%601> , cliquez sur l’une des poignées de cas carré sur le périmètre du **FlowSwitch<T \> ** et faites-la glisser (en maintenant enfoncé le bouton de la souris) sur l’une des poignées qui s’affichent de la même façon autour de l’activité de destination lorsque la souris pointe sur son concepteur. Relâchez le bouton de la souris et une flèche à partir du **FlowSwitch<T \> ** vers le concepteur de destination apparaît et représente ce cas. La valeur par défaut de ce cas s’affiche sur la flèche et peut être modifiée dans **la zone case de la fenêtre** **Propriétés** .

### <a name="the-flowswitcht-properties"></a>Propriétés FlowSwitch \<T>

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.FlowSwitch%601> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Spécifie l’expression qui est évaluée pour déterminer le cas du jeu de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> vers lequel basculer dans le chemin d’exécution.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Spécifie un mappage unique, à partir des résultats possibles obtenus de l'évaluation de la propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, à un jeu d'objets <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Spécifie le mappage lorsque l'évaluation de la propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> ne correspond pas à l'une des valeurs contenues dans l'objet <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Voir aussi

- [Organigramme](../workflow-designer/flowchart-activity-designers.md)
- [Organigramme](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
