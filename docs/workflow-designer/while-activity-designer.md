---
title: Concepteur d’activités Concepteur de flux de travail-while
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6570a80de5be17b2893fc4105f057e655e841881
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649766"
---
# <a name="while-activity-designer"></a>Concepteur d'activités While

L’activité <xref:System.Activities.Statements.While> exécute l’activité contenue dans son <xref:System.Activities.Statements.While.Body%2A>, tandis que la <xref:System.Activities.Statements.While.Condition%2A> spécifiée prend la **valeur true**. L'activité contenue ne peut jamais s'exécuter. Si vous voulez que l'activité contenue soit exécutée au moins une fois, utilisez l'activité <xref:System.Activities.Statements.DoWhile> à la place.

## <a name="while-properties-in-workflow-designer"></a>Propriétés de While dans Workflow Designer

Le tableau suivant répertorie les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.While> et décrit comment elles sont utilisées dans le concepteur.

|Nom de propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.While> dans l'en-tête. La valeur par défaut est While. La valeur peut être modifiée dans la fenêtre **Propriétés** ou directement dans l’en-tête du concepteur d’activités.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Contient l’activité à exécuter lorsque le <xref:System.Activities.Statements.While.Condition%2A> prend la **valeur true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Contient l’expression Visual Basic qui est évaluée pour déterminer si l’activité dans le <xref:System.Activities.Statements.While.Body%2A> doit être exécutée.|

## <a name="see-also"></a>Voir aussi

- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)