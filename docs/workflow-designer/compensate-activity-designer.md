---
title: Concepteur d’activités Concepteur de flux de travail-Compensate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5332b6d9ec087f4e1b127d93563dc0f2fe5fdd15
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876149"
---
# <a name="compensate-activity-designer"></a>Concepteur d'activités Compensate

Le concepteur d’activités **Compensate** est utilisé pour créer et configurer une <xref:System.Activities.Statements.Compensate> activité.

## <a name="the-compensate-activity"></a>Activité Compensate

L'activité <xref:System.Activities.Statements.Compensate> appelle explicitement la propriété <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> pour une activité contenue dans un objet <xref:System.Activities.Statements.CompensableActivity>. Si l'activité <xref:System.Activities.Statements.Compensate> n'est pas utilisée dans la propriété <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> ou <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> d'un objet <xref:System.Activities.Statements.CompensableActivity>, vous devez spécifier la propriété <xref:System.Activities.Statements.Compensate.Target%2A>.

L'objet <xref:System.Activities.Statements.CompensationToken> spécifié par la propriété <xref:System.Activities.Statements.Compensate.Target%2A> fournit un moyen de confirmer ou de compenser explicitement un objet <xref:System.Activities.Statements.CompensableActivity> une fois que le <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> est terminé.

### <a name="using-the-compensate-activity-designer"></a>Utilisation du concepteur d'activités Compensate

Le concepteur d’activités **Compensate** se trouve dans la catégorie **transaction** de la **boîte à outils**. Pour ouvrir la **boîte à outils**, sélectionnez l’onglet **boîte à outils** sur le côté gauche de la concepteur de flux de travail. Vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL** + **ALT** + **X**.

Le concepteur d’activités **Compensate** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . La suppression du concepteur d’activités crée une <xref:System.Activities.Statements.Compensate> activité avec <xref:System.Activities.Activity.DisplayName%2A> compenser par défaut. La <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête du concepteur d’activités **Compensate** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-compensate-properties"></a>Propriétés de Compensate

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CancellationScope> et décrit comment elles sont utilisées dans le concepteur. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans la grille des propriétés ou sur Concepteur de flux de travail surface. Modifiez la <xref:System.Activities.Statements.Compensate.Target%2A> propriété dans la grille des propriétés.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.Compensate>. La valeur par défaut est Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Spécifie l'objet <xref:System.Activities.InArgument%601> qui contient l'objet <xref:System.Activities.Statements.CompensationToken> pour cette activité <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>Voir aussi

- [Transaction](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Concepteur d'activités Compensate](../workflow-designer/compensate-activity-designer.md)
- [Répond](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)