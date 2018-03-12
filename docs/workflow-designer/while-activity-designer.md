---
title: "Concepteur d’activités While | Documents Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 541113e598246cf20f9fe625f57c51f68d7e9ca8
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="while-activity-designer"></a>Concepteur d'activités While
Le <xref:System.Activities.Statements.While> activité s’exécute l’activité contenue dans son <xref:System.Activities.Statements.While.Body%2A> alors que le texte spécifié <xref:System.Activities.Statements.While.Condition%2A> prend la valeur de **true**. L'activité contenue ne peut jamais s'exécuter. Si vous voulez que l'activité contenue soit exécutée au moins une fois, utilisez l'activité <xref:System.Activities.Statements.DoWhile> à la place.

## <a name="while-properties-in-workflow-designer"></a>Propriétés de While dans Workflow Designer
 Le tableau suivant répertorie les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.While> et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.While> dans l'en-tête. La valeur par défaut est While. La valeur peut être modifiée dans le **propriétés** fenêtre ou directement dans l’en-tête du Concepteur d’activité.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.While.Body%2A>|False|Contient l’activité à exécuter pendant que la <xref:System.Activities.Statements.While.Condition%2A> prend la valeur de **true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|True|Contient l'expression [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] évaluée pour déterminer si l'activité dans la propriété <xref:System.Activities.Statements.While.Body%2A> sera exécutée.|

## <a name="see-also"></a>Voir aussi

- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)