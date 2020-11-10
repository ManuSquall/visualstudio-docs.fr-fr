---
title: Concepteur de flux de travail InvokeDelegate
description: Découvrez InvokeDelegate designer et comment vous pouvez utiliser InvokeDelegate Designer pour créer et configurer une activité InvokeDelegate.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InvokeDelegate Designer
- System.Activities.Statements.InvokeDelegate.UI
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
author: TerryGLee
ms.author: tglee
ms.workload:
- multiple
ms.openlocfilehash: a482f23b1df1587e9a1c7e3023bfb0d1737f1fae
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437747"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** Designer est utilisé pour créer et configurer une <xref:System.Activities.Statements.InvokeDelegate> activité.

## <a name="the-invokedelegate-activity"></a>Activité InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> appelle un délégué public.

### <a name="use-the-invokedelegate-activity-designer"></a>Utiliser le concepteur d’activités InvokeDelegate

Accédez au concepteur d’activités **InvokeDelegate** dans la catégorie **primitives** de la **boîte à outils**. Le concepteur d’activités **InvokeDelegate** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . La suppression du concepteur d’activités crée une <xref:System.Activities.Statements.InvokeDelegate> activité avec la valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> InvokeDelegate. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans l’en-tête du concepteur d’activités **InvokeDelegate** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-invokedelegate-properties"></a>Propriétés InvokeDelegate

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.InvokeDelegate> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés, et certaines d’entre elles peuvent être modifiées sur Concepteur de flux de travail surface.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Faux|Nom convivial de l'activité <xref:System.Activities.Statements.InvokeDelegate>. InvokeDelegate est la valeur par défaut.<br /><br /> Bien que le ne <xref:System.Activities.Activity.DisplayName%2A> soit pas strictement obligatoire, il est préférable d’en utiliser un.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Vrai|Nom de <xref:System.Activities.ActivityDelegate> à appeler lorsque l'activité s'exécute. Cette propriété peut être modifiée dans l’aire du concepteur et est obligatoire.|
|<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Faux|Collection d’argument du délégué appelé. Les clés sont les noms des objets de paramètre sur le <xref:System.Activities.ActivityDelegate> , et les valeurs sont les arguments dont les expressions sont évaluées et assignées aux objets de paramètre correspondants. Pour afficher la boîte de dialogue **DelegateArguments** dans laquelle vous pouvez définir cette propriété, cliquez sur le bouton de sélection dans le champ **DelegateArguments** de la grille des propriétés. Cliquez sur le champ **créer un argument** pour ajouter les arguments.|

## <a name="see-also"></a>Voir aussi

- [Procédure : définir et utiliser des délégués d'activité dans le Concepteur de flux de travail](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)