---
title: Concepteur de flux de travail-le concepteur d’activités Persist
description: En savoir plus sur l’activité Persist et sur l’utilisation du concepteur d’activités Persist pour créer et configurer une activité Persist.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 3daa7cef76d2448cc7bcda66a967a3406bb2352c
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435571"
---
# <a name="persist-activity-designer"></a>Concepteur d'activités Persist

Le concepteur d’activités **Persist** est utilisé pour créer et configurer une <xref:System.Activities.Statements.Persist> activité.

## <a name="the-persist-activity"></a>Activité Persist

L'activité <xref:System.Activities.Statements.Persist> enregistre un workflow sur le disque, si possible. L'activité <xref:System.Activities.Statements.Persist> ne peut pas être exécutée dans une zone sans persistance comme, par exemple, dans une activité <xref:System.Activities.Statements.TransactionScope>. Si vous utilisez une <xref:System.Activities.Statements.Persist> activité dans une étendue qui n’est pas de persistance, une exception est levée au moment de l’exécution.

### <a name="using-the-persist-activity-designer"></a>Utilisation du concepteur d'activités Persist

Le concepteur d’activités **Persist** se trouve dans la catégorie **Runtime** de la **boîte à outils** , accessible en cliquant sur l’onglet **boîte à outils** (ou en sélectionnant **boîte à outils** dans le menu **affichage** , ou encore en appuyant sur CTRL + ALT + X).

Le concepteur d’activités **Persist** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . Cela crée une <xref:System.Activities.Statements.Persist> activité avec l’option **DisplayName** par défaut Persist. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans l’en-tête du concepteur d’activités **Persist** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-persist-properties"></a>Propriétés de Persist

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Persist> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d’entre elles peuvent être modifiées sur Concepteur de flux de travail surface.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Faux|Nom convivial de l'activité <xref:System.Activities.Statements.Persist>. La valeur par défaut est Persist. Bien que le nom complet ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|

## <a name="see-also"></a>Voir aussi

- [Runtime](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
