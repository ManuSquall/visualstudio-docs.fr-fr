---
title: Concepteur de flux de travail - Concepteur d’activités CancellationScope
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1032df2f7ebcf4cbc1eae0d4b18757a3f90c4f68
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758055"
---
# <a name="cancellationscope-activity-designer"></a>Concepteur d'activités CancellationScope

Le **CancellationScope** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.CancellationScope> activité.

## <a name="the-cancellationscope-activity"></a>Activité CancellationScope

L'activité <xref:System.Activities.Statements.CancellationScope> vous permet de spécifier une activité pour la logique d'exécution et d'annulation de cette activité.

### <a name="using-the-cancellationscope-activity-designer"></a>Utilisation du concepteur d'activités CancellationScope

Le **CancellationScope** Concepteur d’activités peut être trouvé dans le **Transaction** catégorie de **boîte à outils**. Pour ouvrir **boîte à outils**, sélectionnez le **boîte à outils** onglet du Concepteur de Workflow. Vous pouvez également sélectionner **boîte à outils** à partir de la **vue** menu, ou appuyez sur **Ctrl**+**Alt** + **X**.

Le **CancellationScope** Concepteur d’activités peut être déplacé de **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail chaque fois que les activités sont placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Suppression de la **CancellationScope** Concepteur d’activités crée un <xref:System.Activities.Statements.CancellationScope> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de CancellationScope. Modifier le <xref:System.Activities.Activity.DisplayName%2A> valeur dans l’en-tête de la **CancellationScope** Concepteur d’activités. Vous pouvez également le modifier dans le **DisplayName** case de la grille des propriétés.

### <a name="the-cancellationscope-properties"></a>Propriétés de CancellationScope

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CancellationScope> et décrit comment elles sont utilisées dans le concepteur. Le <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans la grille des propriétés, mais les autres propriétés doivent être modifiées sur l’aire du Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.CancellationScope>. La valeur par défaut est CancellationScope. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Spécifie l'activité pour laquelle la logique d'annulation est fournie. Pour ajouter le <xref:System.Activities.Statements.CancellationScope.Body%2A> activité, déposez une activité de **boîte à outils** dans le **corps** zone sur le **CancellationScope** Concepteur d’activités. Ajoutez le texte d’indication « Déposer l’activité ici ».|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Spécifie l’activité est exécutée s’il existe une annulation. Pour ajouter le <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> activité, déposez une activité de **boîte à outils** dans le **CancellationHandler** zone sur le **CancellationScope** Concepteur d’activités. Ajoutez le texte d’indication « Déposer l’activité ici ».|

## <a name="see-also"></a>Voir aussi

- [Transaction](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compenser](../workflow-designer/compensate-activity-designer.md)
- [Confirmer](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)