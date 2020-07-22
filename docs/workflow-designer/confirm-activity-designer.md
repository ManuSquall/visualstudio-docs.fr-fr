---
title: Concepteur d’activités Concepteur de flux de travail-Confirm
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abd7fedd958072baf23b456f9897ab67c864991d
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876136"
---
# <a name="confirm-activity-designer"></a>Concepteur d'activités Confirm

Le concepteur d’activités **Confirm** est utilisé pour créer et configurer une <xref:System.Activities.Statements.Confirm> activité.

## <a name="the-confirm-activity"></a>Activité Confirm
 L'activité <xref:System.Activities.Statements.Confirm> appelle explicitement la propriété <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> pour une activité contenue dans un objet <xref:System.Activities.Statements.CompensableActivity>. Si l'activité <xref:System.Activities.Statements.Confirm> n'est pas utilisée dans la propriété <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> ou <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> d'un objet <xref:System.Activities.Statements.CompensableActivity>, vous devez spécifier la propriété <xref:System.Activities.Statements.Confirm.Target%2A>.

 L'objet <xref:System.Activities.Statements.CompensationToken> spécifié par la propriété <xref:System.Activities.Statements.Compensate.Target%2A> fournit un moyen de confirmer ou de compenser explicitement un objet <xref:System.Activities.Statements.CompensableActivity> une fois que le <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> est terminé.

### <a name="using-the-confirm-activity-designer"></a>Utilisation du concepteur d'activités Confirm
 Le concepteur d’activités **Confirm** se trouve dans la catégorie **transaction** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** sur le côté gauche de la concepteur de flux de travail. Vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL** + **ALT** + **X**.

 Le concepteur d’activités **Confirm** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . Cette action crée une activité <xref:System.Activities.Statements.Confirm> avec Confirm comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. La <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête du concepteur d’activités **Confirm** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-confirm-properties"></a>Propriétés de Confirm
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Confirm> et décrit comment elles sont utilisées dans le concepteur. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans la grille des propriétés ou sur Concepteur de flux de travail surface, mais la <xref:System.Activities.Statements.Confirm.Target%2A> propriété doit être modifiée dans la grille des propriétés.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.CancellationScope>. La valeur par défaut est Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Spécifie l'objet <xref:System.Activities.InArgument%601> qui contient l'objet <xref:System.Activities.Statements.CompensationToken> pour cette activité <xref:System.Activities.Statements.Confirm>.|

## <a name="see-also"></a>Voir aussi

- [Transaction](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)