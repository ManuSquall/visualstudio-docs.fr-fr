---
title: Concepteur d’activités Concepteur de flux de travail-FlowDecision
description: Découvrez comment le nœud FlowDecision est un nœud conditionnel qui fournit une branche pour le workflow du contrôle dans l’une des deux alternatives.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a70e7e44976df975be721d93e918d7c25d192bf
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437994"
---
# <a name="flowdecision-activity-designer"></a>Concepteur d'activités FlowDecision

Le nœud <xref:System.Activities.Statements.FlowDecision> est un nœud conditionnel qui fournit une branche pour le flux de contrôle dans l'une des deux alternatives suivant qu'une condition spécifiée est satisfaite. Si le flux requiert plusieurs branches, utilisez <xref:System.Activities.Statements.FlowSwitch%601> à la place.

## <a name="the-flowdecision-node"></a>Nœud FlowDecision

Utilisez <xref:System.Activities.Statements.FlowDecision> lorsque le flux peut faire l'objet d'une création de branche dans deux chemins d'accès. Un nœud <xref:System.Activities.Statements.FlowDecision> a un <xref:System.Activities.Statements.FlowDecision.Condition%2A> et un <xref:System.Activities.Statements.FlowNode> associés avec chacun des deux résultats possibles : <xref:System.Activities.Statements.FlowDecision.True%2A> ou <xref:System.Activities.Statements.FlowDecision.False%2A>. La propriété <xref:System.Activities.Statements.FlowDecision.Condition%2A> est évaluée et la valeur de cette évaluation détermine le <xref:System.Activities.Statements.FlowNode> suivant à traiter dans le <xref:System.Activities.Statements.Flowchart>.

### <a name="using-the-flowdecision-designer"></a>Utilisation du concepteur FlowDecision

Le concepteur **FlowDecision** se trouve dans la catégorie **organigramme** de la **boîte à outils** , accessible en cliquant sur l’onglet **boîte à outils** dans la concepteur de flux de travail. Vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL** + **ALT** + **X**.

Le concepteur **FlowDecision** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail dans un concepteur d’activités **Flowchart** . Cela crée une <xref:System.Activities.Statements.FlowDecision> **décision** étiquetée dans l' <xref:System.Activities.Statements.Flowchart> activité. La souris sur le concepteur et les poignées carrées **true** et **false** pour les deux branches s’affichent.

Après avoir fait glisser **FlowDecision** designer et d’autres concepteurs sur l' **organigramme** , les nœuds peuvent être liés ensemble pour spécifier l’ordre d’exécution. Pour créer un lien entre un nœud source (y compris les branches **true** et **false** de **FlowDecision** ) et un nœud de destination, pointez avec la souris sur le concepteur du nœud source et les poignées carrées apparaissent de chaque côté. Cliquez sur l'une des poignées carrées et faites-la glisser en maintenant le bouton de la souris enfoncé jusqu'à l'une des poignées qui s'affiche de la même façon autour du nœud de destination lorsque vous déplacez la souris dessus. Relâchez le bouton de la souris. Un lien est créé entre ces deux nœuds, représenté par une flèche allant du concepteur source au concepteur de destination.

L’expression qui indique le <xref:System.Activities.Statements.FlowDecision.Condition%2A> peut être tapée dans la zone **condition** de la fenêtre **Propriétés** en cliquant à l’endroit où le texte de l’indication indique « entrer une expression VB ».

### <a name="the-flowdecision-properties"></a>Propriétés de FlowDecision

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.FlowDecision> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|Vrai|Condition qui détermine le chemin d'accès emprunté par le contrôle de flux.|
|<xref:System.Activities.Statements.FlowDecision.True%2A>|Faux|Chemin d'accès emprunté par le contrôle de flux si la propriété <xref:System.Activities.Statements.FlowDecision.Condition%2A> est satisfaite.|
|<xref:System.Activities.Statements.FlowDecision.False%2A>|Faux|Chemin d'accès emprunté par le contrôle de flux si la propriété <xref:System.Activities.Statements.FlowDecision.Condition%2A> n'est pas satisfaite.|

## <a name="see-also"></a>Voir aussi

- [Organigramme](../workflow-designer/flowchart-activity-designers.md)
- [Organigramme](../workflow-designer/flowchart-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
