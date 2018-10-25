---
title: Concepteur d’activités de flux de travail concepteur - Confirm
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f6823b564b7ec3da1585810c27db2f97c1b16ae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906531"
---
# <a name="confirm-activity-designer"></a>Concepteur d'activités Confirm

Le **confirmer** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.Confirm> activité.

## <a name="the-confirm-activity"></a>Activité Confirm
 L'activité <xref:System.Activities.Statements.Confirm> appelle explicitement la propriété <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> pour une activité contenue dans un objet <xref:System.Activities.Statements.CompensableActivity>. Si l'activité <xref:System.Activities.Statements.Confirm> n'est pas utilisée dans la propriété <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> ou <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> d'un objet <xref:System.Activities.Statements.CompensableActivity>, vous devez spécifier la propriété <xref:System.Activities.Statements.Confirm.Target%2A>.

 L'objet <xref:System.Activities.Statements.CompensationToken> spécifié par la propriété <xref:System.Activities.Statements.Compensate.Target%2A> fournit un moyen de confirmer ou de compenser explicitement un objet <xref:System.Activities.Statements.CompensableActivity> une fois que le <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> est terminé.

### <a name="using-the-confirm-activity-designer"></a>Utilisation du concepteur d'activités Confirm
 Le **confirmer** Concepteur d’activités peut être trouvé dans le **Transaction** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils**onglet sur le côté gauche du Concepteur de Workflow. Vous pouvez également sélectionner **boîte à outils** à partir de la **vue** menu, ou appuyez sur **Ctrl**+**Alt** + **X**.

 Le **confirmer** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail chaque fois que les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette action crée une activité <xref:System.Activities.Statements.Confirm> avec Confirm comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. Le <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête de la **confirmer** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés.

### <a name="the-confirm-properties"></a>Propriétés de Confirm
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Confirm> et décrit comment elles sont utilisées dans le concepteur. Le <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans la grille des propriétés ou sur l’aire du Concepteur de flux de travail, mais la <xref:System.Activities.Statements.Confirm.Target%2A> propriété doit être modifiée dans la grille des propriétés.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.CancellationScope>. La valeur par défaut est Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Spécifie l'objet <xref:System.Activities.InArgument%601> qui contient l'objet <xref:System.Activities.Statements.CompensationToken> pour cette activité <xref:System.Activities.Statements.Confirm>.|

## <a name="see-also"></a>Voir aussi

- [Transaction](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)