---
title: Concepteur de flux de travail - lors de concepteur d’activités
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81caba883293a59fe67988d34785758340b4705a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987035"
---
# <a name="while-activity-designer"></a>Concepteur d'activités While

Le <xref:System.Activities.Statements.While> activité s’exécute l’activité contenue dans son <xref:System.Activities.Statements.While.Body%2A> while spécifié <xref:System.Activities.Statements.While.Condition%2A> prend la valeur **true**. L'activité contenue ne peut jamais s'exécuter. Si vous voulez que l'activité contenue soit exécutée au moins une fois, utilisez l'activité <xref:System.Activities.Statements.DoWhile> à la place.

## <a name="while-properties-in-workflow-designer"></a>Propriétés de While dans Workflow Designer

Le tableau suivant répertorie les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.While> et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.While> dans l'en-tête. La valeur par défaut est While. La valeur peut être modifiée dans le **propriétés** fenêtre ou directement sur l’en-tête du Concepteur d’activité.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Contient l’activité à exécuter pendant que le <xref:System.Activities.Statements.While.Condition%2A> prend la valeur **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Contient l’expression Visual Basic qui est évaluée pour déterminer si l’activité dans le <xref:System.Activities.Statements.While.Body%2A> doit être exécuté.|

## <a name="see-also"></a>Voir aussi

- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)