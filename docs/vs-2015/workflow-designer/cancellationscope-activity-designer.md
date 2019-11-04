---
title: Concepteur d’activités CancellationScope | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa41d63fa4f67037a8e98e72abc3e338ad894f70
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659182"
---
# <a name="cancellationscope-activity-designer"></a>Concepteur d'activités CancellationScope
Le concepteur d’activités **CancellationScope** permet de créer et de configurer une activité <xref:System.Activities.Statements.CancellationScope>.

## <a name="the-cancellationscope-activity"></a>Activité CancellationScope
 L'activité <xref:System.Activities.Statements.CancellationScope> vous permet de spécifier une activité pour la logique d'exécution et d'annulation de cette activité.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilisation du concepteur d'activités CancellationScope
 Le concepteur d’activités **CancellationScope** se trouve dans la catégorie **transaction** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans la vue)., ou CTRL + ALT + X.)

 Le concepteur d’activités **CancellationScope** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)], là où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. Cette action crée une activité <xref:System.Activities.Statements.CancellationScope> avec CancellationScope comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. La valeur <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **CancellationScope** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-cancellationscope-properties"></a>Propriétés de CancellationScope
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CancellationScope> et décrit comment elles sont utilisées dans le concepteur. La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans la grille des propriétés, mais les autres propriétés doivent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nom de la propriété|Obligatoire|Usage|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.CancellationScope>. La valeur par défaut est CancellationScope. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Spécifie l'activité pour laquelle la logique d'annulation est fournie. Pour ajouter l’activité <xref:System.Activities.Statements.CancellationScope.Body%2A>, déplacez une activité de la boîte **à outils** vers la zone **Body** du concepteur d’activités **CancellationScope** avec le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Spécifie l'activité qui est exécutée dans l'événement d'annulation. Pour ajouter l’activité <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, déposez une activité de la boîte **à outils** dans la zone **CancellationHandler** du concepteur d’activités **CancellationScope** avec le texte d’indication « déposer l’activité ici ».|

## <a name="see-also"></a>Voir aussi
 [Transaction](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [Compensate](../workflow-designer/compensate-activity-designer.md) [Confirm](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)