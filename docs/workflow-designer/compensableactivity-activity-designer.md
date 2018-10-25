---
title: Concepteur de flux de travail - Concepteur d’activités CompensableActivity
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7257e7cc31e0503c7e466bbf4f8c9dd02e5fe15a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836127"
---
# <a name="compensableactivity-activity-designer"></a>Concepteur d'activités CompensableActivity

Le **CompensableActivity** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.CompensableActivity> activité.

## <a name="the-compensableactivity-activity"></a>Activité CompensableActivity
 L'objet <xref:System.Activities.Statements.CompensableActivity> définit une unité de travail qui peut être confirmée ou compensée après avoir été exécutée avec succès.

### <a name="using-the-compensableactivity-activity-designer"></a>Utilisation du concepteur d'activités CompensableActivity
 Le **CompensableActivity** Concepteur d’activités peut être trouvé dans le **Transaction** catégorie de **boîte à outils**. Pour ouvrir **boîte à outils**, sélectionnez le **boîte à outils** onglet sur le côté gauche du Concepteur de Workflow. Vous pouvez également sélectionner **boîte à outils** à partir de la **vue** menu, ou appuyez sur **Ctrl**+**Alt** + **X**.

 Le **CompensableActivity** Concepteur d’activités peut être déplacé de **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail. Vous pouvez déposer le Concepteur d’activités à l’intérieur d’un <xref:System.Activities.Statements.Sequence>. Suppression du Concepteur d’activités crée un <xref:System.Activities.Statements.CompensableActivity> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de CompensableActivity. Modifier le <xref:System.Activities.Activity.DisplayName%2A> valeur dans l’en-tête de la **CompensableActivity** Concepteur d’activités. Il peut également être modifié dans le **DisplayName** case de la grille des propriétés.

### <a name="the-compensableactivity-properties"></a>Propriétés de CompensableActivity
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CompensableActivity> et décrit comment elles sont utilisées dans le concepteur. Le <xref:System.Activities.Activity.DisplayName%2A> et <xref:System.Activities.Activity%601.Result%2A> propriété peut être modifiée dans la grille des propriétés, mais les autres propriétés doivent être modifiées sur l’aire du Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.CompensableActivity>. La valeur par défaut est CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Spécifie la valeur de retour de l'objet <xref:System.Activities.Statements.CompensableActivity>. Cette propriété doit être modifiée dans la grille des propriétés.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Spécifie l'activité pour laquelle la logique de compensation, d'annulation et de confirmation est fournie. Pour ajouter le <xref:System.Activities.Statements.CompensableActivity.Body%2A> activité, déposez une activité de **boîte à outils** dans le **corps** zone sur le **CompensableActivity** Concepteur d’activités. Ajoutez le texte d’indication « Déposer l’activité ici ».|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Spécifie l’activité est exécutée en cas d’annulation. Pour ajouter l’activité, déposez son concepteur de **boîte à outils** dans le **CancellationHandler** zone sur le **CompensableActivity** Concepteur d’activités. Ajoutez le texte d’indication « Déposer l’activité ici ».|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Spécifie l'activité à exécuter lors de la compensation de l'activité <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Ce gestionnaire peut être appelé explicitement à l'aide de l'activité <xref:System.Activities.Statements.Compensate>.<br /><br /> Pour ajouter l’activité, déposez son concepteur d’activités de **boîte à outils** dans le **CompensationHandler** zone sur le **CompensableActivity** Concepteur d’activités. Ajoutez le texte d’indication « Déposer l’activité ici ».|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Spécifie l'activité à exécuter lors de la confirmation de l'activité <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Ce gestionnaire peut être appelé explicitement à l'aide de l'activité <xref:System.Activities.Statements.Confirm>.<br /><br /> Pour ajouter l’activité, déposez son concepteur d’activités de **boîte à outils** dans le **ConfirmationHandler** zone sur le **CompensableActivity** Concepteur d’activités. Ajoutez le texte d’indication « Déposer l’activité ici ».|

## <a name="see-also"></a>Voir aussi

- [Transaction](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)