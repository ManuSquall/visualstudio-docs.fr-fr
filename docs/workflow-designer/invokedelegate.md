---
title: Concepteur de flux de travail InvokeDelegate
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 5227d96e3fad03dd3e3309523a6d2c68a1abdc11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650182"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** Designer est utilisé pour créer et configurer une activité <xref:System.Activities.Statements.InvokeDelegate>.

## <a name="the-invokedelegate-activity"></a>Activité InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> appelle un délégué public.

### <a name="use-the-invokedelegate-activity-designer"></a>Utiliser le concepteur d’activités InvokeDelegate

Accédez au concepteur d’activités **InvokeDelegate** dans la catégorie **primitives** de la **boîte à outils**. Le concepteur d’activités **InvokeDelegate** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. La suppression du concepteur d’activités crée une activité <xref:System.Activities.Statements.InvokeDelegate> avec un <xref:System.Activities.Activity.DisplayName%2A> par défaut de InvokeDelegate. La <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **InvokeDelegate** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-invokedelegate-properties"></a>Propriétés InvokeDelegate

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.InvokeDelegate> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés, et certaines d’entre elles peuvent être modifiées sur Concepteur de flux de travail surface.

|Nom de propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.InvokeDelegate>. InvokeDelegate est la valeur par défaut.<br /><br /> Bien que le <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est préférable d’en utiliser un.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|Nom de <xref:System.Activities.ActivityDelegate> à appeler lorsque l'activité s'exécute. Cette propriété peut être modifiée dans l’aire du concepteur et est obligatoire.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|False|Collection d’argument du délégué appelé. Les clés sont les noms des objets de paramètre sur le <xref:System.Activities.ActivityDelegate>, et les valeurs sont les arguments dont les expressions sont évaluées et assignées aux objets de paramètre correspondants. Pour afficher la boîte de dialogue **DelegateArguments** dans laquelle vous pouvez définir cette propriété, cliquez sur le bouton de sélection dans le champ **DelegateArguments** de la grille des propriétés. Cliquez sur le champ **créer un argument** pour ajouter les arguments.|

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir et utiliser des délégués d’activité dans le Concepteur de flux de travail](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)