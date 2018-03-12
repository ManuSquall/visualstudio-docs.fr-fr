---
title: "FlowSwitch&lt;T&gt; Concepteur d’activités | Documents Microsoft"
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
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 791067ff7e29a3eb63fd77e81a692f93edbda535
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch&lt;T&gt; Concepteur d’activités
L'activité <xref:System.Activities.Statements.FlowSwitch%601> est un nœud conditionnel qui fournit la création de branches pour le flux de contrôle selon un critère de correspondance lorsque plus de deux branches sont requises. Si la création de branches de flux requiert uniquement deux chemins d'accès, utilisez l'activité <xref:System.Activities.Statements.FlowDecision> à la place.

## <a name="the-flowswitcht-activity"></a>Le FlowSwitch < T\> activité
 Le <xref:System.Activities.Statements.FlowSwitch%601> activité contient un <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> qui retourne une valeur de type *T* (spécifié par le paramètre générique) lors de l’évaluation. L'activité contient également un jeu de propriétés <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, qui spécifie un mappage unique, à partir des résultats possibles de cette évaluation, à un jeu d'objets <xref:System.Activities.Statements.FlowNode>. Le <xref:System.Activities.Statements.FlowNode> exécuté est celui dont l’objet de type *T* correspond à la valeur de la liste évaluée <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Un cas <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> peut être fourni (éventuellement) pour le cas dans lequel aucune correspondance n'est obtenue.

### <a name="using-the-flowswitcht-activity-designer"></a>À l’aide de la FlowSwitch\<T > Concepteur d’activités
 Le **FlowSwitch\<T >** Concepteur d’activités peut être trouvé dans le **organigramme** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **Boîte à outils** onglet sur le côté gauche de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

 Le **FlowSwitch\<T >** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] surface au sein d’un **organigramme** Concepteur d’activités. Utilisez le **sélectionner les Types** fenêtre qui s’affiche pour spécifier le type (associé dans le code avec le <xref:System.Activities.Statements.FlowSwitch%601> par son paramètre générique) obtenu à partir de l’évaluation de la <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>. Cette procédure crée un <xref:System.Activities.Statements.FlowSwitch%601> activité intitulée **commutateur** dans le <xref:System.Activities.Statements.Flowchart> activité. Le <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> peuvent être tapés dans le **Expression** zone de la **propriétés** fenêtre en cliquant sur « Entrer une expression VB » où le texte d’information indique que.

 Placez la souris sur le **FlowSwitch\<T >** Concepteur d’activités pour provoquer des poignées carrées utilisées pour la liaison <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> apparaissent autour de ses bords. Après avoir fait glisser le **FlowSwitch < T\>**  Concepteur d’activités et d’autres concepteurs d’activités sur le **organigramme**, le <xref:System.Activities.Activity> objets qu’ils représentent sont prêts à être liés ensemble Pour spécifier l’ordre d’exécution. Pour créer l’un de le <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> associé à la <xref:System.Activities.Statements.FlowSwitch%601>, cliquez sur une des poignées de cas carrées sur le périmètre de la **FlowSwitch < T\>**  et faites-la glisser (en maintenant le bouton de la souris enfoncé) à une poignées de qui apparaît de façon semblable autour de l’activité de destination lorsque la souris pointe sur son concepteur. Relâchez le bouton de la souris et une flèche à partir de la **FlowSwitch < T\>**  au Concepteur de destination apparaît représentant ce cas. La valeur par défaut pour ce cas s’affiche sur la flèche et elle peut être modifiée dans le **cas** zone de la **propriétés** fenêtre.

### <a name="the-flowswitcht-properties"></a>Le FlowSwitch < T\> propriétés
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.FlowSwitch%601> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Spécifie l'expression qui est évaluée pour déterminer le cas du jeu de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> vers lequel basculer dans le chemin d'exécution.|
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Spécifie un mappage unique, à partir des résultats possibles obtenus de l'évaluation de la propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>, à un jeu d'objets <xref:System.Activities.Statements.FlowNode>.|
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Spécifie le mappage lorsque l'évaluation de la propriété <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> ne correspond pas à l'une des valeurs contenues dans l'objet <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|

## <a name="see-also"></a>Voir aussi

- [Organigramme](../workflow-designer/flowchart-activity-designers.md)
- [Organigramme](../workflow-designer/flowchart-activity-designer.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)