---
title: Concepteur d’activités Concepteur de flux de travail-Throw
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe6a530888c7c28c5c1556114db03a6cd7369fe6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649861"
---
# <a name="throw-activity-designer"></a>Concepteur d'activités Throw

Le concepteur d’activités **throw** est utilisé pour créer et configurer une activité <xref:System.Activities.Statements.Throw>.

## <a name="the-throw-activity"></a>Activité Throw

L'activité <xref:System.Activities.Statements.Throw> lève une exception.

### <a name="using-the-throw-activity-designer"></a>Utilisation du concepteur d'activités Throw

Accédez au concepteur d’activités **throw** dans la catégorie **gestion des erreurs** de la **boîte à outils**.

Le concepteur d’activités **throw** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. Cela crée une activité <xref:System.Activities.Statements.Throw> avec un **DisplayName** par défaut de throw. La valeur <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **throw** ou dans la zone **DisplayName** de la grille des propriétés. La propriété <xref:System.Activities.Statements.Throw.Exception%2A> doit être modifiée dans la grille des propriétés.

### <a name="the-throw-properties"></a>Propriétés de Throw

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Throw> et décrit comment elles sont utilisées dans le concepteur.

|Nom de propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.Throw>. La valeur par défaut est Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Exception à lever. Cette exception doit dériver de <xref:System.Exception>. Pour spécifier l'exception, tapez une expression Visual Basic dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi

- [Regroupement](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Concepteur d’activités Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)