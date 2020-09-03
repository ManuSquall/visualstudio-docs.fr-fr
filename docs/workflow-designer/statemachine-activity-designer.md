---
title: Concepteur d’activités Concepteur de flux de travail-StateMachine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: e7a270780a953a6104adc7089a02ff6529106fdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593133"
---
# <a name="statemachine-activity-designer"></a>Concepteur d'activités StateMachine

L'activité <xref:System.Activities.Statements.StateMachine> contient une collection d'états et modélise les workflows à l'aide du modèle familier de machine à états.

## <a name="using-the-statemachine-activity-designer"></a>Utilisation du concepteur d'activités StateMachine

Pour ajouter une <xref:System.Activities.Statements.StateMachine> activité, faites glisser le concepteur d’activités **StateMachine** de la section **machine à États** de la **boîte à outils** et déposez-le sur l’aire de concepteur de flux de travail. Pour ajouter un État enfant à cette <xref:System.Activities.Statements.StateMachine> activité, faites glisser un <xref:System.Activities.Statements.State> ou <xref:System.Activities.Core.Presentation.FinalState> depuis la **boîte à outils** et déposez-le sur le **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Propriétés de l'activité StateMachine dans le concepteur de workflow

Le tableau suivant indique les propriétés  <xref:System.Activities.Statements.StateMachine> qui peuvent être définies à l'aide du concepteur de workflow et explique comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées dans l'aire de conception.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Faux|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.StateMachine> dans l'en-tête. La valeur par défaut est **StateMachine**. La valeur peut être modifiée dans la grille Propriétés ou directement dans l'en-tête du concepteur d'activités. <xref:System.Activities.Activity.DisplayName%2A> est utilisé dans l'exploration à l'aide de la barre de navigation qui est affichée en haut du concepteur de workflow.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|

## <a name="see-also"></a>Voir aussi

- [Organigramme](../workflow-designer/flowchart-activity-designer.md)
- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
