---
title: Concepteur de flux de travail - Concepteur d’activités WriteLine
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0cfe187a77a956c9ebca2649b33dba9218f0fb4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975025"
---
# <a name="writeline-activity-designer"></a>Concepteur d'activités WriteLine

Le **WriteLine** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.WriteLine> activité.

## <a name="the-writeline-activity"></a>Activité WriteLine

L'activité <xref:System.Activities.Statements.WriteLine> écrit du texte dans un objet <xref:System.IO.TextWriter> spécifié. Si aucun objet <xref:System.IO.TextWriter> n'est spécifié, <xref:System.Activities.Statements.WriteLine> écrit le texte dans la console.

### <a name="using-the-writeline-activity-designer"></a>Utilisation du concepteur d'activités WriteLine
 Le **WriteLine** Concepteur d’activités peut être trouvé dans le **Primitives** catégorie de la **boîte à outils**, qui est accessible en cliquant sur les **boîte à outils**onglet du Concepteur de flux de travail (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

 Le **WriteLine** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette action crée une activité <xref:System.Activities.Statements.WriteLine> avec WriteLine comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **WriteLine** Concepteur d’activités ou dans le **DisplayName** zone de la grille des propriétés.

### <a name="the-writeline-properties"></a>Propriétés de WriteLine
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.WriteLine> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées sur l’aire de flux de travail Designerdesigner.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.WriteLine>. La valeur par défaut est WriteLine. Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Texte à écrire. Pour définir la propriété, tapez une expression Visual Basic dans la **texte** zone sur le **WriteLine** activité concepteur ou dans la grille des propriétés.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> dans lequel <xref:System.Activities.Statements.WriteLine> écrit <xref:System.Activities.Statements.WriteLine.Text%2A>. La valeur par défaut est la console.|

## <a name="see-also"></a>Voir aussi

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [affecter](../workflow-designer/assign-activity-designer.md)
- [délai](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)