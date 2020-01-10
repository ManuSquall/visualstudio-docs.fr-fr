---
title: Concepteur d’activités Concepteur de flux de travail-WriteLine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e3b4da69a2d9154f36e42d3b20657e204767872
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593022"
---
# <a name="writeline-activity-designer"></a>Concepteur d'activités WriteLine

Le concepteur d’activités **WriteLine** est utilisé pour créer et configurer une activité <xref:System.Activities.Statements.WriteLine>.

## <a name="the-writeline-activity"></a>Activité WriteLine

L'activité <xref:System.Activities.Statements.WriteLine> écrit du texte dans un objet <xref:System.IO.TextWriter> spécifié. Si aucun objet <xref:System.IO.TextWriter> n'est spécifié, <xref:System.Activities.Statements.WriteLine> écrit le texte dans la console.

### <a name="using-the-writeline-activity-designer"></a>Utilisation du concepteur d'activités WriteLine

Accédez au concepteur d’activités **WriteLine** dans la catégorie **primitives** de la **boîte à outils**. Le concepteur d’activités **WriteLine** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. Cette action crée une activité <xref:System.Activities.Statements.WriteLine> avec WriteLine comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. La <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **WriteLine** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-writeline-properties"></a>Propriétés de WriteLine

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.WriteLine> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d’entre elles peuvent être modifiées sur Concepteur de flux de travail surface.

|Nom de propriété|Obligatoire|Contrôle|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.WriteLine>. La valeur par défaut est WriteLine. Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Texte à écrire. Pour définir la propriété, tapez une expression Visual Basic dans la zone de **texte** sur le concepteur d’activités **WriteLine** ou dans la grille des propriétés.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter> dans lequel <xref:System.Activities.Statements.WriteLine> écrit <xref:System.Activities.Statements.WriteLine.Text%2A>. La valeur par défaut est la console.|

## <a name="see-also"></a>Voir aussi

- [Primitifs](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
