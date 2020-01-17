---
title: Concepteur d’activités Concepteur de flux de travail-TerminateWorkflow
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 078dfb43b5960580327448627a30eec20297d9f3
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76111778"
---
# <a name="terminateworkflow-activity-designer"></a>Concepteur d'activités TerminateWorkflow

Le concepteur d’activités **TerminateWorkflow** permet de créer et de configurer une activité <xref:System.Activities.Statements.TerminateWorkflow>.

## <a name="the-terminateworkflow-activity"></a>Activité TerminateWorkflow

L'activité <xref:System.Activities.Statements.TerminateWorkflow> termine l'exécution d'un workflow.

### <a name="using-the-terminateworkflow-activity-designer"></a>Utilisation du concepteur d'activités TerminateWorkflow

Le concepteur d’activités **TerminateWorkflow** se trouve dans la catégorie **Runtime** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** (ou en sélectionnant **boîte à outils** dans le menu **affichage** , ou encore en appuyant sur CTRL + ALT + X).

Le concepteur d’activités **TerminateWorkflow** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. Cela crée une activité <xref:System.Activities.Statements.TerminateWorkflow> avec un **DisplayName** par défaut de TerminateWorkflow. La <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **TerminateWorkflow** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-terminateworkflow-properties"></a>Propriétés de TerminateWorkflow

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.TerminateWorkflow> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d’entre elles peuvent être modifiées sur Concepteur de flux de travail surface.

|Nom de propriété|Obligatoire|Contrôle|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.TerminateWorkflow>. La valeur par défaut est TerminateWorkflow. Bien que le nom complet ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Exception à lever lorsque le workflow est terminé. Définissez cette propriété dans la grille des propriétés.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Raison qui explique pourquoi le workflow a été terminé. Définissez cette propriété dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)
