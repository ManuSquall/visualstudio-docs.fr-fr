---
title: Concepteur d’activités Concepteur de flux de travail-Throw
description: En savoir plus sur l’activité de Relevez et sur l’utilisation du concepteur d’activités Rethrow pour créer et configurer une activité de nouvelle levée.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9195fc95ac905213b048aa16882ea6584adacd33
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434114"
---
# <a name="rethrow-activity-designer"></a>Concepteur d'activités Rethrow

Le concepteur d’activités **Rethrow** est utilisé pour créer et configurer une <xref:System.Activities.Statements.Rethrow> activité.

## <a name="the-rethrow-activity"></a>Activité de nouvelle levée

L'activité <xref:System.Activities.Statements.Rethrow> lève une exception précédemment levée. Cette activité ne peut être utilisée que dans un gestionnaire <xref:System.Activities.Statements.Catch> dans l'activité <xref:System.Activities.Statements.TryCatch>.

### <a name="use-the-rethrow-activity-designer"></a>Utiliser le concepteur d’activités Rethrow

Accédez au concepteur d’activités **Rethrow** dans la catégorie **gestion des erreurs** de la **boîte à outils**. Le concepteur d’activités **Rethrow** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . La suppression du concepteur d’activités crée une <xref:System.Activities.Statements.Rethrow> activité avec un **DisplayName** par défaut de throw. La <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête du concepteur d’activités **Rethrow** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-rethrow-properties"></a>Propriétés de nouvelle levée

Le tableau suivant présente les <xref:System.Activities.Statements.Rethrow> Propriétés et décrit comment elles sont utilisées dans le concepteur :

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Faux|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.Rethrow>. La valeur par défaut est Rethrow.|

## <a name="see-also"></a>Voir aussi

- [Collection](../workflow-designer/collection-activity-designers.md)
- [Lever](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)
