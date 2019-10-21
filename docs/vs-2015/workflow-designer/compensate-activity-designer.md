---
title: Concepteur d’activités Compensate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 706cd446e931d6a3a065a3e8abfb58b5a90e9152
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656978"
---
# <a name="compensate-activity-designer"></a>Concepteur d'activités Compensate
Le concepteur d’activités **Compensate** est utilisé pour créer et configurer une activité <xref:System.Activities.Statements.Compensate>.

## <a name="the-compensate-activity"></a>Activité Compensate
 L'activité <xref:System.Activities.Statements.Compensate> appelle explicitement la propriété <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> pour une activité contenue dans un objet <xref:System.Activities.Statements.CompensableActivity>. Si l'activité <xref:System.Activities.Statements.Compensate> n'est pas utilisée dans la propriété <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> ou <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> d'un objet <xref:System.Activities.Statements.CompensableActivity>, vous devez spécifier la propriété <xref:System.Activities.Statements.Compensate.Target%2A>.

 L'objet <xref:System.Activities.Statements.CompensationToken> spécifié par la propriété <xref:System.Activities.Statements.Compensate.Target%2A> fournit un moyen de confirmer ou de compenser explicitement un objet <xref:System.Activities.Statements.CompensableActivity> une fois que le <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> est terminé.

### <a name="using-the-compensate-activity-designer"></a>Utilisation du concepteur d'activités Compensate
 Le concepteur d’activités **Compensate** se trouve dans la catégorie **transaction** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** sur le côté gauche de l' [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans la  **Menu Affichage** , ou CTRL + ALT + X.)

 Le concepteur d’activités **Compensate** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)], là où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. Cette action crée une activité <xref:System.Activities.Statements.Compensate> avec Compensate comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. La valeur <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **Compensate** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-compensate-properties"></a>Propriétés de Compensate
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CancellationScope> et décrit comment elles sont utilisées dans le concepteur. La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans la grille des propriétés ou dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)], mais la propriété <xref:System.Activities.Statements.Compensate.Target%2A> doit être modifiée dans l'aire de conception.

|Nom de propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.Compensate>. La valeur par défaut est Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Spécifie l'objet <xref:System.Activities.InArgument%601> qui contient l'objet <xref:System.Activities.Statements.CompensationToken> pour cette activité <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>Voir aussi
 Concepteur d’activités de [transaction](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [Compensate](../workflow-designer/compensate-activity-designer.md) [confirmer](../workflow-designer/confirm-activity-designer.md) [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)