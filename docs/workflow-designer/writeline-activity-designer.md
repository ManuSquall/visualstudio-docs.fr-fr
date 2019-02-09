---
title: Concepteur de flux de travail - Concepteur d’activités WriteLine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17dd6e3c617749d82533d8bccb7f0caaa073ac26
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930322"
---
# <a name="writeline-activity-designer"></a>Concepteur d'activités WriteLine

Le **WriteLine** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.WriteLine> activité.

## <a name="the-writeline-activity"></a>Activité WriteLine

L'activité <xref:System.Activities.Statements.WriteLine> écrit du texte dans un objet <xref:System.IO.TextWriter> spécifié. Si aucun objet <xref:System.IO.TextWriter> n'est spécifié, <xref:System.Activities.Statements.WriteLine> écrit le texte dans la console.

### <a name="using-the-writeline-activity-designer"></a>Utilisation du concepteur d'activités WriteLine

Accès le **WriteLine** Concepteur d’activités dans le **Primitives** catégorie de la **boîte à outils**. Le **WriteLine** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail chaque fois que les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette action crée une activité <xref:System.Activities.Statements.WriteLine> avec WriteLine comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **WriteLine** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés.

### <a name="the-writeline-properties"></a>Propriétés de WriteLine

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.WriteLine> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées sur l’aire du Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.WriteLine>. La valeur par défaut est WriteLine. Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Texte à écrire. Pour définir la propriété, tapez une expression Visual Basic dans le **texte** zone sur le **WriteLine** activité concepteur ou dans la grille des propriétés.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> dans lequel <xref:System.Activities.Statements.WriteLine> écrit <xref:System.Activities.Statements.WriteLine.Text%2A>. La valeur par défaut est la console.|

## <a name="see-also"></a>Voir aussi

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)