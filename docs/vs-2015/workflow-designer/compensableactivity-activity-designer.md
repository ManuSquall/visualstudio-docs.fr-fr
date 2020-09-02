---
title: Concepteur d’activités CompensableActivity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2bc28c4586912d7c253c9629c2af0eefd30e47e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656991"
---
# <a name="compensableactivity-activity-designer"></a>Concepteur d'activités CompensableActivity
Le concepteur d’activités **CompensableActivity** permet de créer et de configurer une <xref:System.Activities.Statements.CompensableActivity> activité.

## <a name="the-compensableactivity-activity"></a>Activité CompensableActivity
 L'objet <xref:System.Activities.Statements.CompensableActivity> définit une unité de travail qui peut être confirmée ou compensée après avoir été exécutée avec succès.

### <a name="using-the-compensableactivity-activity-designer"></a>Utilisation du concepteur d'activités CompensableActivity
 Le concepteur d’activités **CompensableActivity** se trouve dans la catégorie **transaction** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** sur le côté gauche de [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans le menu **affichage** , ou encore en appuyant sur CTRL + ALT + X).

 Le concepteur d’activités **CompensableActivity** peut être déplacé de la **boîte à outils** et déposé dans l’aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)] , là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . Cette action crée une activité <xref:System.Activities.Statements.CompensableActivity> avec CompensableActivity comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. La <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête du concepteur d’activités **CompensableActivity** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-compensableactivity-properties"></a>Propriétés de CompensableActivity
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CompensableActivity> et décrit comment elles sont utilisées dans le concepteur. Les propriétés <xref:System.Activities.Activity.DisplayName%2A> et <xref:System.Activities.Activity%601.Result%2A> peuvent être modifiées dans la grille des propriétés, mais les autres propriétés doivent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nom de la propriété|Obligatoire|Usage|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.CompensableActivity>. La valeur par défaut est CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Spécifie la valeur de retour de l'objet <xref:System.Activities.Statements.CompensableActivity>. Cette propriété doit être modifiée dans la grille des propriétés.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Spécifie l'activité pour laquelle la logique de compensation, d'annulation et de confirmation est fournie. Pour ajouter l' <xref:System.Activities.Statements.CompensableActivity.Body%2A> activité, déplacez une activité de la boîte **à outils** vers la zone **Body** sur le concepteur d’activités **CompensableActivity** avec le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Spécifie l'activité qui est exécutée dans l'événement d'annulation. Pour ajouter l’activité, déposez son concepteur de la boîte **à outils** dans la zone **CancellationHandler** du concepteur d’activités **CompensableActivity** avec le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Spécifie l'activité à exécuter lors de la compensation de l'activité <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Ce gestionnaire peut être appelé explicitement à l'aide de l'activité <xref:System.Activities.Statements.Compensate>.<br /><br /> Pour ajouter l’activité, déposez son concepteur d’activités de la boîte **à outils** dans la zone **CompensationHandler** du concepteur d’activités **CompensableActivity** avec le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Spécifie l'activité à exécuter lors de la confirmation de l'activité <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Ce gestionnaire peut être appelé explicitement à l'aide de l'activité <xref:System.Activities.Statements.Confirm>.<br /><br /> Pour ajouter l’activité, déposez son concepteur d’activités de la boîte **à outils** dans la zone **ConfirmationHandler** du concepteur d’activités **CompensableActivity** avec le texte d’indication « déposer l’activité ici ».|

## <a name="see-also"></a>Voir aussi
 [Transaction](../workflow-designer/transaction-activity-designers.md) [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md) [compensation](../workflow-designer/compensate-activity-designer.md) [Confirm](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md) de la transaction de compensation