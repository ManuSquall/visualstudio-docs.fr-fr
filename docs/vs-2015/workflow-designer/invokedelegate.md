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
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc35aec714255b467431488936605fb37009db9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659006"
---
# <a name="invokedelegate"></a>InvokeDelegate

**InvokeDelegate** Designer est utilisé pour créer et configurer une <xref:System.Activities.Statements.InvokeDelegate> activité.

## <a name="the-invokedelegate-activity"></a>Activité InvokeDelegate

<xref:System.Activities.Statements.InvokeDelegate> appelle un délégué public.

### <a name="using-the-invokedelegate-activity-designer"></a>Utilisation du concepteur d'activités InvokeDelegate

Le concepteur d’activités **InvokeDelegate** se trouve dans la catégorie **primitives** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans le menu **affichage** , ou encore Ctrl + Alt + X).

Le concepteur d’activités **InvokeDelegate** peut être déplacé de la **boîte à outils** et déposé dans l’aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)] , là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . Cette opération crée une activité <xref:System.Activities.Statements.InvokeDelegate> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut InvokeDelegate. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans l’en-tête du concepteur d’activités **InvokeDelegate** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-invokedelegate-properties"></a>Propriétés d'InvokeDelegate

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.InvokeDelegate> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines peuvent être modifiés dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nom de la propriété|Obligatoire|Usage|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Faux|Nom convivial de l'activité <xref:System.Activities.Statements.InvokeDelegate>. InvokeDelegate est la valeur par défaut.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|Vrai|Nom de <xref:System.Activities.ActivityDelegate> à appeler lorsque l'activité s'exécute. Cette propriété peut être modifiée dans l'aire du concepteur. Il s'agit d'une propriété obligatoire.|
|<<xref:System.Activities.Statements.InvokeDelegate.DelegateArguments%2A>|Faux|Collection d’argument du délégué appelé. Les clés sont les noms des objets <xref:System.Activities.DelegateArgument> de l'<xref:System.Activities.ActivityDelegate>, tandis que les valeurs sont les arguments dont les expressions sont évaluées et affectées aux objets <xref:System.Activities.DelegateArgument> correspondants. Dans la grille des propriétés, cliquez sur le bouton de sélection dans le champ **DelegateArguments** , il affiche la boîte de dialogue **DelegateArguments** pour vous permettre de définir cette propriété. Cliquez sur le champ **créer un argument** pour ajouter les arguments.|

## <a name="see-also"></a>Voir aussi

- [Procédure : définir et utiliser des délégués d'activité dans le Concepteur de flux de travail](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)