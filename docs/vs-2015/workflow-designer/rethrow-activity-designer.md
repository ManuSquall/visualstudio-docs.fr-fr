---
title: Concepteur d’activités Rethrow | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c65469242a60c64d6f31bfaea4fdbbf2d5251a34
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663367"
---
# <a name="rethrow-activity-designer"></a>Concepteur d'activités Rethrow
Le concepteur d’activités **Rethrow** est utilisé pour créer et configurer une activité <xref:System.Activities.Statements.Rethrow>.

## <a name="the-rethrow-activity"></a>Activité Rethrow
 L'activité <xref:System.Activities.Statements.Rethrow> lève une exception précédemment levée. Cette activité ne peut être utilisée que dans un gestionnaire <xref:System.Activities.Statements.Catch> dans l'activité <xref:System.Activities.Statements.TryCatch>.

### <a name="using-the-rethrow-activity-designer"></a>Utilisation du concepteur d'activités Rethrow
 Le concepteur d’activités **Rethrow** se trouve dans la **catégorie gestion des erreurs** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** sur le côté gauche de l' [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans la  **Menu Affichage** ou CTRL + ALT + X.)

 Le concepteur d’activités **Rethrow** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)], là où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. Cela crée une activité <xref:System.Activities.Statements.Rethrow> avec un **DisplayName** par défaut de throw. La valeur <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **Rethrow** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-rethrow-properties"></a>Propriétés de Rethrow
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Rethrow> et décrit comment elles sont utilisées dans le concepteur.

|Nom de propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.Rethrow>. La valeur par défaut est Rethrow.|

## <a name="see-also"></a>Voir aussi
 [TryCatch](../workflow-designer/trycatch-activity-designer.md) d' [exception](../workflow-designer/throw-activity-designer.md) de la [collection](../workflow-designer/collection-activity-designers.md)