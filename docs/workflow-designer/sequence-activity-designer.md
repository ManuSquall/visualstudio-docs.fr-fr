---
title: Concepteur d’activités Concepteur de flux de travail-Sequence
description: Découvrez comment l’activité Sequence contient une collection ordonnée d’activités enfants qu’elle exécute dans l’ordre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9e7e6e9114405bc1575e0256dd63211a4fb6d08
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433971"
---
# <a name="sequence-activity-designer"></a>Concepteur d'activités Sequence

L'activité <xref:System.Activities.Statements.Sequence> contient une collection ordonnée d'activités enfants qu'elle exécute dans l'ordre.

Une autre façon d'exécuter un ensemble d'activités dans l'ordre consiste à utiliser une activité <xref:System.Activities.Statements.Flowchart>. Envisagez d’utiliser l' [organigramme](../workflow-designer/flowchart-activity-designer.md) lorsque vous avez un flux de programme de création de branches ou de boucle simple que vous souhaitez modéliser diagramme.

## <a name="using-the-sequence-activity-designer"></a>Utilisation du concepteur d'activités Sequence

Pour ajouter une <xref:System.Activities.Statements.Sequence> activité, faites glisser le concepteur d’activités **Sequence** de la **boîte à outils** et déposez-le sur l’aire de concepteur de flux de travail. Pour ajouter une activité enfant à cette <xref:System.Activities.Statements.Sequence> activité, faites glisser une autre activité de la **boîte à outils** et déposez-la sur le triangle dans la zone avec le texte d’indication « déposer l’activité ici ».

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité Sequence dans le concepteur de workflow

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Sequence> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Faux|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.Sequence> dans l'en-tête. Sequence est la valeur par défaut. La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en-tête du concepteur d'activités.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|

## <a name="see-also"></a>Voir aussi

- [Organigramme](../workflow-designer/flowchart-activity-designer.md)
- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)