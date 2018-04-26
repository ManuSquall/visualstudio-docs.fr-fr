---
title: Concepteur de flux de travail - Concepteur d’activités Rethrow
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d441724afa1cf481bc15e2a43e6ec744a951187
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="rethrow-activity-designer"></a>Concepteur d'activités Rethrow

Le **Rethrow** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.Rethrow> activité.

## <a name="the-rethrow-activity"></a>Activité Rethrow
 L'activité <xref:System.Activities.Statements.Rethrow> lève une exception précédemment levée. Cette activité ne peut être utilisée que dans un gestionnaire <xref:System.Activities.Statements.Catch> dans l'activité <xref:System.Activities.Statements.TryCatch>.

### <a name="using-the-rethrow-activity-designer"></a>Utilisation du concepteur d'activités Rethrow
 Le **Rethrow** Concepteur d’activités peut être trouvé dans le **gestion des erreurs** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils**onglet sur le côté gauche du Concepteur de flux de travail (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

 Le **Rethrow** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette opération crée un <xref:System.Activities.Statements.Rethrow> activité avec une valeur par défaut **DisplayName** throw. Le <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête de la **Rethrow** Concepteur d’activités ou dans le **DisplayName** zone de la grille des propriétés.

### <a name="the-rethrow-properties"></a>Propriétés de Rethrow
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Rethrow> et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.Rethrow>. La valeur par défaut est Rethrow.|

## <a name="see-also"></a>Voir aussi

- [Collection](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)