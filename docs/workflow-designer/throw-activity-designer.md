---
title: Concepteur d’activités throw | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82080c7ebc03b863dcd1fbebe9eb9923ba4fae3c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="throw-activity-designer"></a>Concepteur d'activités Throw
Le **lever** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.Throw> activité.

## <a name="the-throw-activity"></a>Activité Throw
 L'activité <xref:System.Activities.Statements.Throw> lève une exception.

### <a name="using-the-throw-activity-designer"></a>Utilisation du concepteur d'activités Throw
 Le **lever** Concepteur d’activités peut être trouvé dans le **gestion des erreurs** catégorie de la **boîte à outils**, qui est accessible en cliquant sur les **boîte à outils**onglet sur le côté gauche de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

 Le **lever** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] surface, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette opération crée un <xref:System.Activities.Statements.Throw> activité avec une valeur par défaut **DisplayName** throw. Le <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête de la **lever** Concepteur d’activités ou dans le **DisplayName** zone de la grille des propriétés. La propriété <xref:System.Activities.Statements.Throw.Exception%2A> doit être modifiée dans la grille des propriétés.

### <a name="the-throw-properties"></a>Propriétés de Throw
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Throw> et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.Throw>. La valeur par défaut est Throw.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Exception à lever. Cette exception doit dériver de <xref:System.Exception>. Pour spécifier l'exception, tapez une expression Visual Basic dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi

- [Collection](../workflow-designer/collection-activity-designers.md)
- [rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Concepteur d’activités Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)