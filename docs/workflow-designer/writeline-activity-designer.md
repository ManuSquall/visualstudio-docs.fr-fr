---
title: Concepteur d’activités WriteLine | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b52bf3401e609076043f42a8df3544313d6e8a74
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="writeline-activity-designer"></a>Concepteur d'activités WriteLine
Le **WriteLine** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.WriteLine> activité.

## <a name="the-writeline-activity"></a>Activité WriteLine
 L'activité <xref:System.Activities.Statements.WriteLine> écrit du texte dans un objet <xref:System.IO.TextWriter> spécifié. Si aucun objet <xref:System.IO.TextWriter> n'est spécifié, <xref:System.Activities.Statements.WriteLine> écrit le texte dans la console.

### <a name="using-the-writeline-activity-designer"></a>Utilisation du concepteur d'activités WriteLine
 Le **WriteLine** Concepteur d’activités peut être trouvé dans le **Primitives** catégorie de la **boîte à outils**, qui est accessible en cliquant sur les **boîte à outils**onglet de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

 Le **WriteLine** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] surface, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette action crée une activité <xref:System.Activities.Statements.WriteLine> avec WriteLine comme <xref:System.Activities.Activity.DisplayName%2A> par défaut. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **WriteLine** Concepteur d’activités ou dans le **DisplayName** zone de la grille des propriétés.

### <a name="the-writeline-properties"></a>Propriétés de WriteLine
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.WriteLine> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés et certaines d'entre elles peuvent être modifiées dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].

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