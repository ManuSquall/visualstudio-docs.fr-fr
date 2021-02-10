---
title: Concepteur de flux de travail-concepteur d’activités Flowchart
description: Découvrez comment vous pouvez utiliser l’activité Flowchart pour créer des flux de travail qui définissent et gèrent des contrôles de flux complexes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c9c46ae3dcc0063c7a2664e032fba14ce320af18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961298"
---
# <a name="flowchart-activity-designer"></a>Concepteur d'activités d'organigramme

L'activité <xref:System.Activities.Statements.Flowchart> permet de créer des flux de travail qui définissent et gèrent des contrôles de flux complexes. Un <xref:System.Activities.Statements.Flowchart> peut être créé dans le code ou à l’aide de concepteur de flux de travail. Cette rubrique décrit l’expérience Concepteur de flux de travail. Le concepteur d’activités de flux de travail Concepteur de flux de travail permet aux développeurs de créer des flux de travail de manière naturelle.

## <a name="the-flowchart-activity"></a>Activité Flowchart

<xref:System.Activities.Statements.Flowchart> spécifie une propriété <xref:System.Activities.Statements.Flowchart.StartNode%2A> unique exécutée lorsque le flux de travail démarre et utilise un réseau de propriétés <xref:System.Activities.Statements.Flowchart.Nodes%2A> liées pour créer des boucles arbitraires ou détourner le flux d'exécution ailleurs dans le flux de travail à un moment donné.

### <a name="using-the-flowchart-activity-designer"></a>Utilisation du concepteur d'activités Flowchart

Le concepteur d’activités **Flowchart** se trouve dans la catégorie **organigramme** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** dans la concepteur de flux de travail. Vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL** + **ALT** + **X**.

Le concepteur d’activités **Flowchart** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les concepteurs d’activités sont généralement placés, en tant qu’activité racine ou en tant qu’enfant d’une autre activité de flux de contrôle. Si le concepteur d’activités **Flowchart** est déposé sur une surface concepteur de flux de travail vide, il crée une <xref:System.Activities.Statements.Flowchart> activité, qui s’affiche par défaut dans une vue développée dans laquelle le nœud de démarrage qui démarre l’exécution est représenté par une boule verte. Si le concepteur d’activités **Flowchart** est déposé dans une autre activité de flux de contrôle, il s’affiche dans une vue réduite qui peut être développée en double-cliquant sur le concepteur d’activités **Flowchart** . Toutes les activités de la **boîte à outils** peuvent être déplacées directement sur le concepteur d’activités **Flowchart** , y compris les autres activités de flux de contrôle.

Une fois que vous avez fait glisser plusieurs concepteurs d’activités sur le canevas Concepteur de flux de travail, les <xref:System.Activities.Activity> objets qu’ils représentent peuvent être liés entre eux pour spécifier l’ordre d’exécution. Pour créer un lien entre une activité source et une activité de destination, pointez la souris sur le concepteur de l'activité source pour faire apparaître des poignées carrées sur chacun de ses côtés. Cliquez sur l'une des poignées carrées et faites-la glisser, en maintenant le bouton de la souris enfoncé, vers l'une des poignées qui s'affiche de manière similaire autour de l'activité de destination lorsque vous pointez dessus avec la souris. Relâchez le bouton de la souris, un lien est créé entre ces deux activités, représenté par une flèche du concepteur source au concepteur de destination.

### <a name="flowchart-activity-properties"></a>Propriétés de l'activité Flowchart

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Flowchart> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom d'affichage du concepteur d'activités dans l'en-tête. La valeur par défaut est Flowchart. La valeur peut être modifiée dans la fenêtre **Propriétés** ou directement dans l’en-tête du concepteur d’activités.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|Collection de variables dont l'étendue est limitée par cet objet <xref:System.Activities.Statements.Flowchart> pour partager l'état entre ses activités enfants.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|Objet <xref:System.Activities.Statements.FlowNode> exécuté lorsque <xref:System.Activities.Statements.Flowchart> démarre.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|Contient la collection d'objets <xref:System.Activities.Statements.FlowNode> dans <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>Voir aussi

- [Organigramme](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)
