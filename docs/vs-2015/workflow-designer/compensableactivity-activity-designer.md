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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f11743e0027866fd45687f716f1989e98020c68e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952055"
---
# <a name="compensableactivity-activity-designer"></a>Concepteur d'activités CompensableActivity
Le **CompensableActivity** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.CompensableActivity> activité.  
  
## <a name="the-compensableactivity-activity"></a>Activité CompensableActivity  
 L'objet <xref:System.Activities.Statements.CompensableActivity> définit une unité de travail qui peut être confirmée ou compensée après avoir été exécutée avec succès.  
  
### <a name="using-the-compensableactivity-activity-designer"></a>Utilisation du concepteur d'activités CompensableActivity  
 Le **CompensableActivity** Concepteur d’activités peut être trouvé dans le **Transaction** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils**  onglet sur le côté gauche de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)  
  
 Le **CompensableActivity** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette action crée une activité <xref:System.Activities.Statements.CompensableActivity> avec CompensableActivity comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. Le <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête de la **CompensableActivity** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés.  
  
### <a name="the-compensableactivity-properties"></a>Propriétés de CompensableActivity  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CompensableActivity> et décrit comment elles sont utilisées dans le concepteur. Les propriétés <xref:System.Activities.Activity.DisplayName%2A> et <xref:System.Activities.Activity%601.Result%2A> peuvent être modifiées dans la grille des propriétés, mais les autres propriétés doivent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.CompensableActivity>. La valeur par défaut est CompensableActivity.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Spécifie la valeur de retour de l'objet <xref:System.Activities.Statements.CompensableActivity>. Cette propriété doit être modifiée dans la grille des propriétés.|  
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Spécifie l'activité pour laquelle la logique de compensation, d'annulation et de confirmation est fournie. Pour ajouter le <xref:System.Activities.Statements.CompensableActivity.Body%2A> activité, déposez une activité de la **boîte à outils** dans le **corps** zone sur le **CompensableActivity** Concepteur d’activités avec le texte d’indication « Drop activité ici ».|  
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Spécifie l'activité qui est exécutée dans l'événement d'annulation. Pour ajouter l’activité, déposez son concepteur de la **boîte à outils** dans le **CancellationHandler** zone sur le **CompensableActivity** Concepteur d’activités avec le texte d’indication « Drop Activité ici ».|  
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Spécifie l'activité à exécuter lors de la compensation de l'activité <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Ce gestionnaire peut être appelé explicitement à l'aide de l'activité <xref:System.Activities.Statements.Compensate>.<br /><br /> Pour ajouter l’activité, déposez son concepteur d’activités de la **boîte à outils** dans le **CompensationHandler** zone sur le **CompensableActivity** Concepteur d’activités avec le texte d’indication » Déposer l’activité ici ».|  
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Spécifie l'activité à exécuter lors de la confirmation de l'activité <xref:System.Activities.Statements.CompensableActivity.Body%2A>. Ce gestionnaire peut être appelé explicitement à l'aide de l'activité <xref:System.Activities.Statements.Confirm>.<br /><br /> Pour ajouter l’activité, déposez son concepteur d’activités de la **boîte à outils** dans le **ConfirmationHandler** zone sur le **CompensableActivity** Concepteur d’activités avec le texte d’indication » Déposer l’activité ici ».|  
  
## <a name="see-also"></a>Voir aussi  
 [Transaction](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [Compenser](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)