---
title: Concepteur d’activités Concepteur de flux de travail-while
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85f8d6c442982fff47a679e8fc2ccc04ee515a9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650515"
---
# <a name="dowhile-activity-designer"></a>Concepteur d'activités DoWhile

L’activité <xref:System.Activities.Statements.DoWhile> exécute l’activité contenue dans son <xref:System.Activities.Statements.DoWhile.Body%2A> au moins une fois, jusqu’à ce qu’une condition spécifiée ait la **valeur false**. Si vous devez exécuter zéro ou plusieurs fois l'activité contenue dans le corps d'une boucle, utilisez plutôt l'activité <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Propriétés de DoWhile dans Workflow Designer

Le tableau suivant répertorie les propriétés d’activité <xref:System.Activities.Statements.DoWhile> les plus utiles et décrit comment les utiliser dans le concepteur :

|Nom de propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Activité à exécuter lorsque la condition a la **valeur true**. Pour ajouter l’activité <xref:System.Activities.Statements.DoWhile.Body%2A>, déplacez une activité de la boîte à outils vers la zone **Body** sur le concepteur d’activités en **cours** avec le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Condition à évaluer après chaque itération de la boucle. Pour définir la <xref:System.Activities.Statements.DoWhile.Condition%2A>, tapez une expression de Visual Basic dans la zone **condition** du concepteur d’activités en **cours** ou dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi

- [While](../workflow-designer/while-activity-designer.md)
- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)