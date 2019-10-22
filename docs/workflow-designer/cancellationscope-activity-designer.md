---
title: Concepteur d’activités Concepteur de flux de travail-CancellationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a2fd36d81f774ca48cca170b8a4a256d73cf1f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650702"
---
# <a name="cancellationscope-activity-designer"></a>Concepteur d'activités CancellationScope

Le concepteur d’activités **CancellationScope** permet de créer et de configurer une activité <xref:System.Activities.Statements.CancellationScope>.

## <a name="the-cancellationscope-activity"></a>Activité CancellationScope

L'activité <xref:System.Activities.Statements.CancellationScope> vous permet de spécifier une activité pour la logique d'exécution et d'annulation de cette activité.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilisation du concepteur d'activités CancellationScope

Le concepteur d’activités **CancellationScope** se trouve dans la catégorie **transaction** de la **boîte à outils**. Pour ouvrir la **boîte à outils**, sélectionnez l’onglet **boîte à outils** de la concepteur de flux de travail. Vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL** +**ALT** +**X**.

Le concepteur d’activités **CancellationScope** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. La suppression du concepteur d’activités **CancellationScope** crée une activité <xref:System.Activities.Statements.CancellationScope> avec un <xref:System.Activities.Activity.DisplayName%2A> par défaut de CancellationScope. Modifiez la valeur de <xref:System.Activities.Activity.DisplayName%2A> dans l’en-tête du concepteur d’activités **CancellationScope** . Vous pouvez également le modifier dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-cancellationscope-properties"></a>Propriétés de CancellationScope

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CancellationScope> et décrit comment elles sont utilisées dans le concepteur. La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans la grille des propriétés, mais les autres propriétés doivent être modifiées sur Concepteur de flux de travail surface.

|Nom de propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.CancellationScope>. La valeur par défaut est CancellationScope. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Spécifie l'activité pour laquelle la logique d'annulation est fournie. Pour ajouter l’activité <xref:System.Activities.Statements.CancellationScope.Body%2A>, déposez une activité de la boîte **à outils** dans la zone **corps** du concepteur d’activités **CancellationScope** . Ajoutez le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Spécifie l’activité qui est exécutée en cas d’annulation. Pour ajouter l’activité <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, déposez une activité de la boîte **à outils** dans la zone **CancellationHandler** du concepteur d’activités **CancellationScope** . Ajoutez le texte d’indication « déposer l’activité ici ».|

## <a name="see-also"></a>Voir aussi

- [Transaction](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)