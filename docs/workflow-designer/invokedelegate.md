---
title: Concepteur de flux de travail - InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e3d802000bede1a654b088fb80b134a36a0185be
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758525"
---
# <a name="invokedelegate"></a>InvokeDelegate

Le **InvokeDelegate** concepteur est utilisé pour créer et configurer un <xref:System.Activities.Statements.InvokeDelegate> activité.

## <a name="the-invokedelegate-activity"></a>L’activité InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> appelle un délégué public.

### <a name="use-the-invokedelegate-activity-designer"></a>Utiliser le Concepteur d’activités InvokeDelegate

Accès le **InvokeDelegate** Concepteur d’activités dans le **Primitives** catégorie de la **boîte à outils**. Le **InvokeDelegate** Concepteur d’activités peut être déplacé de la **boîte à outils** et supprimé une session sur l’aire du Concepteur de flux de travail, quel que soit les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Suppression du Concepteur d’activités crée un <xref:System.Activities.Statements.InvokeDelegate> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de InvokeDelegate. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **InvokeDelegate** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés.

### <a name="the-invokedelegate-properties"></a>Les propriétés d’InvokeDelegate

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.InvokeDelegate> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiés sur l’aire du Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.InvokeDelegate>. InvokeDelegate est la valeur par défaut.<br /><br /> Bien que le <xref:System.Activities.Activity.DisplayName%2A> n’est pas strictement obligatoire, il est préférable d’utiliser un.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nom de <xref:System.Activities.ActivityDelegate> à appeler lorsque l'activité s'exécute. Cette propriété peut être modifiée sur l’aire du concepteur et est obligatoire.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Collection d’argument du délégué appelé. Les clés sont les noms des objets de paramètre sur le <xref:System.Activities.ActivityDelegate>, et les valeurs sont les arguments dont les expressions sont évaluées et affectées aux objets de paramètre correspondant. Pour afficher le **DelegateArguments** boîte de dialogue où vous pouvez définir cette propriété, cliquez sur le bouton de sélection dans le **DelegateArguments** champ de la grille des propriétés. Cliquez sur le **créer un Argument** champ pour ajouter les arguments.|

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir et utiliser des délégués d’activité dans le Concepteur de flux de travail](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)