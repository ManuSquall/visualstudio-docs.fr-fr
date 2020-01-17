---
title: Concepteur de flux de travail-le concepteur d’activités Persist
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75236d7955cba6b8c62b9a4504f02c66cebe4062
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114770"
---
# <a name="persist-activity-designer"></a>Concepteur d'activités Persist

Le concepteur d’activités **Persist** est utilisé pour créer et configurer une activité <xref:System.Activities.Statements.Persist>.

## <a name="the-persist-activity"></a>Activité Persist

L'activité <xref:System.Activities.Statements.Persist> enregistre un workflow sur le disque, si possible. L'activité <xref:System.Activities.Statements.Persist> ne peut pas être exécutée dans une zone sans persistance comme, par exemple, dans une activité <xref:System.Activities.Statements.TransactionScope>. Si vous utilisez une activité <xref:System.Activities.Statements.Persist> dans une étendue sans persistance, une exception est levée au moment de l’exécution.

### <a name="using-the-persist-activity-designer"></a>Utilisation du concepteur d'activités Persist

Le concepteur d’activités **Persist** se trouve dans la catégorie **Runtime** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** (ou en sélectionnant **boîte à outils** dans le menu **affichage** , ou encore en appuyant sur CTRL + ALT + X).

Le concepteur d’activités **Persist** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. Cela crée une activité <xref:System.Activities.Statements.Persist> avec l’option **DisplayName** par défaut Persist. La <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **Persist** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-persist-properties"></a>Propriétés de Persist

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Persist> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d’entre elles peuvent être modifiées sur Concepteur de flux de travail surface.

|Nom de propriété|Obligatoire|Contrôle|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Persist>. La valeur par défaut est Persist. Bien que le nom complet ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|

## <a name="see-also"></a>Voir aussi

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
