---
title: Le Concepteur de flux de travail - conserver le Concepteur d’activités
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04c7989f5cc37ec295f9fa778f2120dd372fd99a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="persist-activity-designer"></a>Concepteur d'activités Persist

Le **Persist** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.Persist> activité.

## <a name="the-persist-activity"></a>Activité Persist

L'activité <xref:System.Activities.Statements.Persist> enregistre un workflow sur le disque, si possible. L'activité <xref:System.Activities.Statements.Persist> ne peut pas être exécutée dans une zone sans persistance comme, par exemple, dans une activité <xref:System.Activities.Statements.TransactionScope>. Si vous utilisez une activité <xref:System.Activities.Statements.Persist> dans une étendue sans persistance, une exception est levée au moment de l'exécution.

### <a name="using-the-persist-activity-designer"></a>Utilisation du concepteur d'activités Persist

Le **Persist** Concepteur d’activités peut être trouvé dans le **Runtime** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils** onglet (ou bien, sélectionnez **boîte à outils** à partir de la **vue** menu ou CTRL + ALT + X.)

Le **Persist** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette opération crée un <xref:System.Activities.Statements.Persist> activité avec une valeur par défaut **DisplayName** Persist. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **Persist** Concepteur d’activités ou dans le **DisplayName** zone de la grille des propriétés.

### <a name="the-persist-properties"></a>Propriétés de Persist

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Persist> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées sur l’aire du Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Persist>. La valeur par défaut est Persist. Bien que le nom complet ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|

## <a name="see-also"></a>Voir aussi

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)