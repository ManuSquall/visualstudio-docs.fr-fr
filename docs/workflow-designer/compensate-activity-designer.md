---
title: Concepteur de flux de travail - de concepteur d’activités Compensate
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1bca40a093f228f22919b7734e387a4bc191316c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756368"
---
# <a name="compensate-activity-designer"></a>Concepteur d'activités Compensate

Le **compenser** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.Compensate> activité.

## <a name="the-compensate-activity"></a>Activité Compensate

L'activité <xref:System.Activities.Statements.Compensate> appelle explicitement la propriété <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> pour une activité contenue dans un objet <xref:System.Activities.Statements.CompensableActivity>. Si l'activité <xref:System.Activities.Statements.Compensate> n'est pas utilisée dans la propriété <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> ou <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> d'un objet <xref:System.Activities.Statements.CompensableActivity>, vous devez spécifier la propriété <xref:System.Activities.Statements.Compensate.Target%2A>.

L'objet <xref:System.Activities.Statements.CompensationToken> spécifié par la propriété <xref:System.Activities.Statements.Compensate.Target%2A> fournit un moyen de confirmer ou de compenser explicitement un objet <xref:System.Activities.Statements.CompensableActivity> une fois que le <xref:System.Activities.Statements.CompensableActivity.Body%2A> de <xref:System.Activities.Statements.CompensableActivity> est terminé.

### <a name="using-the-compensate-activity-designer"></a>Utilisation du concepteur d'activités Compensate

Le **compenser** Concepteur d’activités peut être trouvé dans le **Transaction** catégorie de la **boîte à outils**. Pour ouvrir **boîte à outils**, sélectionnez le **boîte à outils** onglet sur le côté gauche du Concepteur de Workflow. Vous pouvez également sélectionner **boîte à outils** à partir de la **vue** menu, ou appuyez sur **Ctrl**+**Alt** + **X**.

Le **compenser** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail chaque fois que les activités sont placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Suppression du Concepteur d’activités crée un <xref:System.Activities.Statements.Compensate> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de compenser. Le <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête de la **compenser** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés.

### <a name="the-compensate-properties"></a>Propriétés de Compensate

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CancellationScope> et décrit comment elles sont utilisées dans le concepteur. Le <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans la grille des propriétés ou sur l’aire du Concepteur de flux de travail. Modifier le <xref:System.Activities.Statements.Compensate.Target%2A> propriété dans la grille des propriétés.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.Compensate>. La valeur par défaut est Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Spécifie l'objet <xref:System.Activities.InArgument%601> qui contient l'objet <xref:System.Activities.Statements.CompensationToken> pour cette activité <xref:System.Activities.Statements.Compensate>.|

## <a name="see-also"></a>Voir aussi

- [Transaction](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Concepteur d’activités Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirmer](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)