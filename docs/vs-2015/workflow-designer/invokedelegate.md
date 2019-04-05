---
title: InvokeDelegate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30281d8cd5d5ed94ed89a980006f9618292a778d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953542"
---
# <a name="invokedelegate"></a>InvokeDelegate

Le **InvokeDelegate** concepteur est utilisé pour créer et configurer un <xref:System.Activities.Statements.InvokeDelegate> activité.

## <a name="the-invokedelegate-activity"></a>Activité InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> appelle un délégué public.

### <a name="using-the-invokedelegate-activity-designer"></a>Utilisation du concepteur d'activités InvokeDelegate

Le **InvokeDelegate** Concepteur d’activités peut être trouvé dans le **Primitives** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils** onglet [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

Le **InvokeDelegate** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette opération crée une activité <xref:System.Activities.Statements.InvokeDelegate> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut InvokeDelegate. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **InvokeDelegate** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés.

### <a name="the-invokedelegate-properties"></a>Propriétés d'InvokeDelegate

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.InvokeDelegate> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiés dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.InvokeDelegate>. InvokeDelegate est la valeur par défaut.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nom de <xref:System.Activities.ActivityDelegate> à appeler lorsque l'activité s'exécute. Cette propriété peut être modifiée dans l'aire du concepteur. Il s'agit d'une propriété obligatoire.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Collection d’argument du délégué appelé. Les clés sont les noms des objets <xref:System.Activities.DelegateArgument> de l'<xref:System.Activities.ActivityDelegate>, tandis que les valeurs sont les arguments dont les expressions sont évaluées et affectées aux objets <xref:System.Activities.DelegateArgument> correspondants. Dans la grille des propriétés, cliquez sur le bouton de sélection dans le **DelegateArguments** champ, il affiche le **DelegateArguments** boîte de dialogue pour vous permettre de définir cette propriété. Cliquez sur le **créer un Argument** champ pour ajouter les arguments.|

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir et utiliser des délégués d’activité dans le concepteur de workflow](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)