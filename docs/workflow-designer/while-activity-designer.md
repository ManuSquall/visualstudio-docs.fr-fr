---
title: Concepteur d’activités Concepteur de flux de travail-while
description: Découvrez comment l’activité While exécute l’activité contenue dans son corps, tandis que la condition spécifiée prend la valeur true.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9447d32f17283e7123e2f99490acc49c1613360d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837994"
---
# <a name="while-activity-designer"></a>Concepteur d'activités While

L' <xref:System.Activities.Statements.While> activité exécute l’activité contenue dans son, <xref:System.Activities.Statements.While.Body%2A> tandis que le spécifié <xref:System.Activities.Statements.While.Condition%2A> prend la **valeur true**. L'activité contenue ne peut jamais s'exécuter. Si vous voulez que l'activité contenue soit exécutée au moins une fois, utilisez l'activité <xref:System.Activities.Statements.DoWhile> à la place.

## <a name="while-properties-in-workflow-designer"></a>Propriétés de While dans Workflow Designer

Le tableau suivant répertorie les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.While> et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.While> dans l'en-tête. La valeur par défaut est While. La valeur peut être modifiée dans la fenêtre **Propriétés** ou directement dans l’en-tête du concepteur d’activités.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Contient l’activité à exécuter pendant que <xref:System.Activities.Statements.While.Condition%2A> prend la **valeur true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Contient l’expression Visual Basic qui est évaluée pour déterminer si l’activité dans le <xref:System.Activities.Statements.While.Body%2A> doit être exécutée.|

## <a name="see-also"></a>Voir aussi

- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
