---
title: Concepteur de flux de travail - Concepteur d’activités TerminateWorkflow
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5dfd7438a14f0bcbedcf5cdc5add78020604c355
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975557"
---
# <a name="terminateworkflow-activity-designer"></a>Concepteur d'activités TerminateWorkflow

Le **TerminateWorkflow** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.TerminateWorkflow> activité.

## <a name="the-terminateworkflow-activity"></a>Activité TerminateWorkflow

L'activité <xref:System.Activities.Statements.TerminateWorkflow> termine l'exécution d'un workflow.

### <a name="using-the-terminateworkflow-activity-designer"></a>Utilisation du concepteur d'activités TerminateWorkflow

Le **TerminateWorkflow** Concepteur d’activités peut être trouvé dans le **Runtime** catégorie de la **boîte à outils**, qui est accessible en cliquant sur les **boîte à outils** onglet (ou bien, sélectionnez **boîte à outils** à partir de la **vue** menu ou CTRL + ALT + X.)

Le **TerminateWorkflow** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette opération crée un <xref:System.Activities.Statements.TerminateWorkflow> activité avec une valeur par défaut **DisplayName** de TerminateWorkflow. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **TerminateWorkflow** Concepteur d’activités ou dans le **DisplayName** zone de la grille des propriétés.

### <a name="the-terminateworkflow-properties"></a>Propriétés de TerminateWorkflow

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.TerminateWorkflow> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées sur l’aire du Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.TerminateWorkflow>. La valeur par défaut est TerminateWorkflow. Bien que le nom complet ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Exception à lever lorsque le workflow est terminé. Définissez cette propriété dans la grille des propriétés.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Raison qui explique pourquoi le workflow a été terminé. Définissez cette propriété dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [Conserver](../workflow-designer/persist-activity-designer.md)