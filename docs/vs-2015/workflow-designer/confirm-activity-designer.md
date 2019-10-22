---
title: Confirmer le concepteur d’activités | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b3835c6cb537e7ac74862ac4a6794dd7b0bd5003
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656964"
---
# <a name="confirm-activity-designer"></a>Concepteur d'activités Confirm
Le concepteur d’activités **Confirm** est utilisé pour créer et configurer une activité <xref:System.Activities.Statements.Confirm>.

## <a name="the-confirm-activity"></a>Activité Confirm
 L'activité <xref:System.Activities.Statements.Confirm> appelle explicitement la propriété <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> pour une activité contenue dans un objet <xref:System.Activities.Statements.CompensableActivity>. Si l'activité <xref:System.Activities.Statements.Confirm> n'est pas utilisée dans la propriété <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> ou <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> d'un objet <xref:System.Activities.Statements.CompensableActivity>, vous devez spécifier la propriété <xref:System.Activities.Statements.Confirm.Target%2A>.

 L'objet <xref:System.Activities.Statements.CompensationToken> spécifié par la propriété <xref:System.Activities.Statements.Compensate.Target%2A> fournit un moyen de confirmer ou de compenser explicitement un objet <xref:System.Activities.Statements.CompensableActivity> une fois que le <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> est terminé.

### <a name="using-the-confirm-activity-designer"></a>Utilisation du concepteur d'activités Confirm
 Le concepteur d’activités **Confirm** se trouve dans la catégorie **transaction** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** sur le côté gauche de l' [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans la **vue.** menu ou CTRL + ALT + X.)

 Le concepteur d’activités **Confirm** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)], là où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. Cette action crée une activité <xref:System.Activities.Statements.Confirm> avec Confirm comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. La valeur <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **Confirm** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-confirm-properties"></a>Propriétés de Confirm
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Confirm> et décrit comment elles sont utilisées dans le concepteur. La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans la grille des propriétés ou dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)], mais la propriété <xref:System.Activities.Statements.Confirm.Target%2A> doit être modifiée dans l'aire de conception.

|Nom de propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.CancellationScope>. La valeur par défaut est Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Spécifie l'objet <xref:System.Activities.InArgument%601> qui contient l'objet <xref:System.Activities.Statements.CompensationToken> pour cette activité <xref:System.Activities.Statements.Confirm>.|

## <a name="see-also"></a>Voir aussi
 [Transaction](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [Compensate](../workflow-designer/compensate-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)