---
title: Concepteur d’activités Concepteur de flux de travail-CompensableActivity
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec70c22ae195dc6dd58aa2cfa893cee35fe6ca8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597098"
---
# <a name="compensableactivity-activity-designer"></a>Concepteur d'activités CompensableActivity

Le concepteur d’activités **CompensableActivity** permet de créer et de configurer une activité <xref:System.Activities.Statements.CompensableActivity>.

## <a name="the-compensableactivity-activity"></a>Activité CompensableActivity
 L'objet <xref:System.Activities.Statements.CompensableActivity> définit une unité de travail qui peut être confirmée ou compensée après avoir été exécutée avec succès.

### <a name="using-the-compensableactivity-activity-designer"></a>Utilisation du concepteur d'activités CompensableActivity
 Le concepteur d’activités **CompensableActivity** se trouve dans la catégorie **transaction** de la **boîte à outils**. Pour ouvrir la **boîte à outils**, sélectionnez l’onglet **boîte à outils** sur le côté gauche de la concepteur de flux de travail. Vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL**+**ALT**+**X**.

 Le concepteur d’activités **CompensableActivity** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail. Vous pouvez supprimer le concepteur d’activités à l’intérieur d’un <xref:System.Activities.Statements.Sequence>. La suppression du concepteur d’activités crée une activité <xref:System.Activities.Statements.CompensableActivity> avec un <xref:System.Activities.Activity.DisplayName%2A> par défaut de CompensableActivity. Modifiez la valeur de <xref:System.Activities.Activity.DisplayName%2A> dans l’en-tête du concepteur d’activités **CompensableActivity** . Il peut également être modifié dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-compensableactivity-properties"></a>Propriétés de CompensableActivity
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CompensableActivity> et décrit comment elles sont utilisées dans le concepteur. La propriété <xref:System.Activities.Activity.DisplayName%2A> et <xref:System.Activities.Activity%601.Result%2A> peut être modifiée dans la grille des propriétés, mais les autres propriétés doivent être modifiées sur l’aire de Concepteur de flux de travail.

|Nom de propriété|Obligatoire|Contrôle|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.CompensableActivity>. La valeur par défaut est CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Spécifie la valeur de retour de l'objet <xref:System.Activities.Statements.CompensableActivity>. Cette propriété doit être modifiée dans la grille des propriétés.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Spécifie l'activité pour laquelle la logique de compensation, d'annulation et de confirmation est fournie. Pour ajouter l’activité <xref:System.Activities.Statements.CompensableActivity.Body%2A>, déposez une activité de la boîte **à outils** dans la zone **corps** du concepteur d’activités **CompensableActivity** . Ajoutez le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Spécifie l’activité qui est exécutée en cas d’annulation. Pour ajouter l’activité, déposez son concepteur de la boîte **à outils** dans la zone **CancellationHandler** du concepteur d’activités **CompensableActivity** . Ajoutez le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Spécifie l'activité à exécuter lors de la compensation de l'activité <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Ce gestionnaire peut être appelé explicitement à l'aide de l'activité <xref:System.Activities.Statements.Compensate>.<br /><br /> Pour ajouter l’activité, déposez son concepteur d’activités de la boîte **à outils** dans la zone **CompensationHandler** du concepteur d’activités **CompensableActivity** . Ajoutez le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Spécifie l'activité à exécuter lors de la confirmation de l'activité <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Ce gestionnaire peut être appelé explicitement à l'aide de l'activité <xref:System.Activities.Statements.Confirm>.<br /><br /> Pour ajouter l’activité, déposez son concepteur d’activités de la boîte **à outils** dans la zone **ConfirmationHandler** du concepteur d’activités **CompensableActivity** . Ajoutez le texte d’indication « déposer l’activité ici ».|

## <a name="see-also"></a>Voir aussi

- [Transaction](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)
