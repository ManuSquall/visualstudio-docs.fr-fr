---
title: Concepteur d’activités Concepteur de flux de travail-Pick
description: Découvrez comment l’activité Pick fournit un workflow de contrôle basé sur les événements et exécute l’une des différentes branches en réponse à un événement de déclenchement.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9968a00a1e4530e22abe25819c9e3d5188bcefa
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434244"
---
# <a name="pick-activity-designer"></a>Concepteur d'activités Pick

L'activité <xref:System.Activities.Statements.Pick> fournit un flux de contrôle basé sur les événements. Elle exécute l'une des différentes branches en réponse à un événement de déclenchement.

## <a name="the-pick-activity"></a>Activité Pick

Une activité <xref:System.Activities.Statements.Pick> contient une collection d’objets <xref:System.Activities.Statements.PickBranch>, dont l’un peut être exécuté par l’activité <xref:System.Activities.Statements.Pick> en raison d’un événement entrant qui sert de déclencheur. De cette façon Concepteur de flux de travail fournit une modélisation de workflow basée sur les événements. Chaque <xref:System.Activities.Statements.PickBranch> contient une propriété <xref:System.Activities.Statements.PickBranch.Trigger%2A> et une propriété <xref:System.Activities.Statements.PickBranch.Action%2A>. Au début de l' <xref:System.Activities.Statements.Pick> exécution d’une activité, toutes les activités de déclencheur des <xref:System.Activities.Statements.PickBranch> éléments sont planifiées. À l'issue de la première activité, l'activité d'action correspondante est planifiée et toutes les autres activités de déclencheur sont annulées.

### <a name="how-to-use-the-pick-activity-designer"></a>Comment utiliser le concepteur d'activités Pick

Accédez au concepteur d’activités **Pick** dans la catégorie **Flow Control** de la **boîte à outils**. Le concepteur d’activités **Pick** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les concepteurs d’activités sont généralement placés, par exemple dans un concepteur d’activités **Sequence** . Après l’avoir supprimée dans Concepteur de flux de travail, elle crée une <xref:System.Activities.Statements.Pick> activité, qui, par défaut, contient deux <xref:System.Activities.Statements.PickBranch> activités vides en tant qu’éléments avec les noms d’affichage Branch1 et Branch2. Ces <xref:System.Activities.Statements.PickBranch.DisplayName%2A> valeurs de propriétés respectives peuvent être modifiées dans l’en-tête du concepteur d’activités **PickBranch** ou dans la fenêtre **Propriétés** pour chaque branche.

Il existe deux façons d’ajouter <xref:System.Activities.Statements.PickBranch> des activités à la collection d’un <xref:System.Activities.Statements.Pick> objet : en glissant et déposant le concepteur **PickBranch** à partir de la **boîte à outils** ou en utilisant le menu contextuel à partir de l’aire de conception **Pick** . Pour plus d’informations, consultez la rubrique [PickBranch](../workflow-designer/pickbranch-activity-designer.md) . Notez que le seul élément qui peut être placé à l’intérieur d’un concepteur d’activités **Pick** est un concepteur d’activités **PickBranch** .

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité Pick dans le concepteur de workflow

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Pick> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Faux|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.Pick> dans l'en-tête. La valeur par défaut est Pick. La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en-tête du concepteur d'activités.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|

## <a name="see-also"></a>Voir aussi

- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
- [Activité Pick](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Utilisation de l’activité Pick](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)