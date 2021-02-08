---
title: Concepteur de flux de travail-concepteur d’activités TransactionScope
description: Découvrez comment vous pouvez utiliser le concepteur d’activités TransactionScope pour créer et configurer une activité TransactionScope.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TransactionScope.UI
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 234e6c2d0349cf610d9ba22d53ce59e3768ad64e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838007"
---
# <a name="transactionscope-activity-designer"></a>Concepteur d'activités TransactionScope

Le concepteur d’activités **TransactionScope** permet de créer et de configurer une <xref:System.Activities.Statements.TransactionScope> activité.

## <a name="the-transactionscope-activity"></a>Activité TransactionScope

L’activité <xref:System.Activities.Statements.TransactionScope> exécute l’activité contenue dans une transaction unique. La transaction est validée lorsque l'activité <xref:System.Activities.Statements.TransactionScope.Body%2A> et tous les autres participants de la transaction sont terminés.

### <a name="using-the-transactionscope-activity-designer"></a>Utilisation du concepteur d'activités TransactionScope

Accédez au concepteur d’activités **TransactionScope** dans la catégorie **transaction** de la **boîte à outils**. Le concepteur d’activités **TransactionScope** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . Cette action crée une activité <xref:System.Activities.Statements.TransactionScope> avec TransactionScope comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. La <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête du concepteur d’activités **TransactionScope** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-transactionscope-properties"></a>Propriétés de TransactionScope

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.TransactionScope> et décrit comment elles sont utilisées dans le concepteur. Les <xref:System.Activities.Activity.DisplayName%2A> <xref:System.Activities.Statements.TransactionScope.Body%2A> Propriétés et peuvent être modifiées sur Concepteur de flux de travail surface. En revanche, les autres propriétés doivent être modifiées dans la grille des propriétés.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.TransactionScope>. La valeur par défaut est TransactionScope. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Spécifie l’activité à exécuter dans une transaction unique. Pour ajouter l' <xref:System.Activities.Statements.TransactionScope.Body%2A> activité, déplacez une activité de la boîte **à outils** vers la zone **Body** du concepteur d’activités **TransactionScope** avec le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Spécifie la valeur <xref:System.Transactions.IsolationLevel> de cet objet <xref:System.Activities.Statements.TransactionScope>.|
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Spécifie l’intervalle de temps (au format 00:00:00, qui correspond à heures:minutes:secondes) dont dispose la transaction pour se terminer. La valeur par défaut est égale à 1 minute (00:01:00).|
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure*>|True|Spécifie la valeur qui indique si le flux de travail doit être abandonné en cas d’abandon de la transaction.|

## <a name="see-also"></a>Voir aussi

- [Transaction](../workflow-designer/transaction-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirmer](../workflow-designer/confirm-activity-designer.md)
