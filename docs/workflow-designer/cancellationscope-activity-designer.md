---
title: Concepteur d’activités Concepteur de flux de travail-CancellationScope
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6d1067b529dffec5a4e6a1f21d5489c32311c07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76112507"
---
# <a name="cancellationscope-activity-designer"></a>Concepteur d'activités CancellationScope

Le concepteur d’activités **CancellationScope** permet de créer et de configurer une <xref:System.Activities.Statements.CancellationScope> activité.

## <a name="the-cancellationscope-activity"></a>Activité CancellationScope

L'activité <xref:System.Activities.Statements.CancellationScope> vous permet de spécifier une activité pour la logique d'exécution et d'annulation de cette activité.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilisation du concepteur d'activités CancellationScope

Le concepteur d’activités **CancellationScope** se trouve dans la catégorie **transaction** de la **boîte à outils**. Pour ouvrir la **boîte à outils**, sélectionnez l’onglet **boîte à outils** de la concepteur de flux de travail. Vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL** + **ALT** + **X**.

Le concepteur d’activités **CancellationScope** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . La suppression du concepteur d’activités **CancellationScope** crée une <xref:System.Activities.Statements.CancellationScope> activité avec CancellationScope comme valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> . Modifiez la <xref:System.Activities.Activity.DisplayName%2A> valeur dans l’en-tête du concepteur d’activités **CancellationScope** . Vous pouvez également le modifier dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-cancellationscope-properties"></a>Propriétés de CancellationScope

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CancellationScope> et décrit comment elles sont utilisées dans le concepteur. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans la grille des propriétés, mais les autres propriétés doivent être modifiées sur Concepteur de flux de travail surface.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.CancellationScope>. La valeur par défaut est CancellationScope. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Spécifie l'activité pour laquelle la logique d'annulation est fournie. Pour ajouter l' <xref:System.Activities.Statements.CancellationScope.Body%2A> activité, déposez une activité de la boîte **à outils** dans la zone **corps** du concepteur d’activités **CancellationScope** . Ajoutez le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Spécifie l’activité qui est exécutée en cas d’annulation. Pour ajouter l' <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> activité, déposez une activité de la boîte **à outils** dans la zone **CancellationHandler** du concepteur d’activités **CancellationScope** . Ajoutez le texte d’indication « déposer l’activité ici ».|

## <a name="see-also"></a>Voir aussi

- [Transaction](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirmer](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
