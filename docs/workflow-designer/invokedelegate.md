---
title: InvokeDelegate | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 93e41d98b156b6314158a1cc99e368092b0cf494
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="invokedelegate"></a>InvokeDelegate
Le **InvokeDelegate** concepteur est utilisé pour créer et configurer un <xref:System.Activities.Statements.InvokeDelegate> activité.

## <a name="the-invokedelegate-activity"></a>Activité InvokeDelegate
 <xref:System.Activities.Statements.InvokeDelegate> appelle un délégué public.

### <a name="using-the-invokedelegate-activity-designer"></a>Utilisation du concepteur d'activités InvokeDelegate
 Le **InvokeDelegate** Concepteur d’activités peut être trouvé dans le **Primitives** catégorie de la **boîte à outils**, qui est accessible en cliquant sur les **boîte à outils** onglet [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

 Le **InvokeDelegate** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] surface là activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette opération crée une activité <xref:System.Activities.Statements.InvokeDelegate> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut InvokeDelegate. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **InvokeDelegate** Concepteur d’activités ou dans le **DisplayName** zone de la grille des propriétés.

### <a name="the-invokedelegate-properties"></a>Propriétés d'InvokeDelegate
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.InvokeDelegate> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiés dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.InvokeDelegate>. InvokeDelegate est la valeur par défaut.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nom de <xref:System.Activities.ActivityDelegate> à appeler lorsque l'activité s'exécute. Cette propriété peut être modifiée dans l'aire du concepteur. Il s'agit d'une propriété obligatoire.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Collection d’argument du délégué appelé. Les clés sont les noms des objets de paramètre sur le <xref:System.Activities.ActivityDelegate> et les valeurs sont les arguments dont les expressions sont évaluées et affectées aux objets de paramètre correspondant. Dans la grille des propriétés, cliquez sur le bouton de sélection dans le **DelegateArguments** champ, il affiche la **DelegateArguments** boîte de dialogue pour vous permettre de définir cette propriété. Cliquez sur le **créer un Argument** champ pour ajouter les arguments.|

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir et utiliser des délégués d’activité dans le Concepteur de flux de travail](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)