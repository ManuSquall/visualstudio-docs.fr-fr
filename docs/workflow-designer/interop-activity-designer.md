---
title: Concepteur d’activités Concepteur de flux de travail-Interop
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8047df3787c0871e369b6079e4f0cc80f6d93949
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650207"
---
# <a name="interop-activity-designer"></a>Concepteur d'activités Interop

Le concepteur d’activités **Interop** est utilisé pour créer et configurer une activité <xref:System.Activities.Statements.Interop>.

## <a name="the-interop-activity"></a>Activité Interop

L'activité <xref:System.Activities.Statements.Interop> gère l'exécution des types qui dérivent de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> dans un workflow.

### <a name="use-the-interop-activity-designer"></a>Utiliser le concepteur d’activités Interop

Le concepteur d’activités **Interop** se trouve dans la catégorie **migration** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** . vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL** +**ALT** +**X**.

La catégorie de [migration](../workflow-designer/migration-activity-designers.md) qui contient l’activité <xref:System.Activities.Statements.Interop> s’affiche uniquement dans la **boîte à outils** si votre projet cible .NET Framework 4 (complète) ou version ultérieure. Si nécessaire, vous pouvez modifier la version du Framework ciblée par votre projet.

Le concepteur d’activités **Interop** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. La suppression du concepteur d’activités **Interop** crée une activité <xref:System.Activities.Statements.Interop> avec un **DisplayName** par défaut de l’interopérabilité. Vous pouvez modifier les <xref:System.Activities.Activity.DisplayName%2A> dans l’en-tête du concepteur d’activités **Interop** ou dans la zone **DisplayName** de la grille des propriétés.

Cliquez sur le **bouton Parcourir pour parcourir** le texte dans la zone **ActivityType** , dans le concepteur d’activités **Interop** ou dans la grille des propriétés, pour ouvrir la boîte de dialogue **Parcourir et sélectionner un type .net** . Seuls les types pour les activités Workflow 3,0 ou workflow 3,5 sont affichés. Autrement dit, seuls les types dérivés de <xref:System.Workflow.ComponentModel.Activity> sont affichés. Pour plus d’informations sur l’utilisation de cette zone pour spécifier un type, consultez [Parcourir et sélectionner un type .net, boîte de dialogue](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Propriétés d'Interop

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Interop> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou sur l’aire de Concepteur de flux de travail.

|Nom de propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Interop>. La valeur par défaut est **Interop**. Bien que le nom d’affichage ne soit pas obligatoire, il est recommandé d’en fournir un.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Spécifie le type de l'activité contenue par l'activité <xref:System.Activities.Statements.Interop>. Le type spécifié doit dériver d'<xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Voir aussi

- [Migration](../workflow-designer/migration-activity-designers.md)