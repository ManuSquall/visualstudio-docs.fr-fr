---
title: Concepteur d’activités CancellationScope | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 125e9fd934ce40d2a6633daa62b817628306daa3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229890"
---
# <a name="cancellationscope-activity-designer"></a>Concepteur d'activités CancellationScope
Le **CancellationScope** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.CancellationScope> activité.  
  
## <a name="the-cancellationscope-activity"></a>Activité CancellationScope  
 L'activité <xref:System.Activities.Statements.CancellationScope> vous permet de spécifier une activité pour la logique d'exécution et d'annulation de cette activité.  
  
### <a name="using-the-cancellationscope-activity-designer"></a>Utilisation du concepteur d'activités CancellationScope  
 Le **CancellationScope** Concepteur d’activités peut être trouvé dans le **Transaction** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils**  onglet de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)  
  
 Le **CancellationScope** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette action crée une activité <xref:System.Activities.Statements.CancellationScope> avec CancellationScope comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. Le <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête de la **CancellationScope** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés.  
  
### <a name="the-cancellationscope-properties"></a>Propriétés de CancellationScope  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.CancellationScope> et décrit comment elles sont utilisées dans le concepteur. La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans la grille des propriétés, mais les autres propriétés doivent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial facultatif de l'activité <xref:System.Activities.Statements.CancellationScope>. La valeur par défaut est CancellationScope. Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Spécifie l'activité pour laquelle la logique d'annulation est fournie. Pour ajouter le <xref:System.Activities.Statements.CancellationScope.Body%2A> activité, déposez une activité de la **boîte à outils** dans le **corps** zone sur le **CancellationScope** Concepteur d’activités avec le texte d’indication « Drop Activité ici ».|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Spécifie l'activité qui est exécutée dans l'événement d'annulation. Pour ajouter le <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> activité, déposez une activité de la **boîte à outils** dans le **CancellationHandler** zone sur le **CancellationScope** Concepteur d’activités avec indicateur texte « Déposer l’activité ici ».|  
  
## <a name="see-also"></a>Voir aussi  
 [Transaction](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compenser](../workflow-designer/compensate-activity-designer.md)   
 [Confirmer](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)