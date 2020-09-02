---
title: Concepteur d’activités Concepteur de flux de travail-while
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c56a9ab8b46f8f7ee36875dda507cb9f288136cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86875603"
---
# <a name="dowhile-activity-designer"></a>Concepteur d'activités DoWhile

L' <xref:System.Activities.Statements.DoWhile> activité exécute l’activité contenue dans son <xref:System.Activities.Statements.DoWhile.Body%2A> au moins une fois, jusqu’à ce qu’une condition spécifiée ait la **valeur false**. Si vous devez exécuter zéro ou plusieurs fois l'activité contenue dans le corps d'une boucle, utilisez plutôt l'activité <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Propriétés de DoWhile dans Workflow Designer

Le tableau suivant répertorie les <xref:System.Activities.Statements.DoWhile> propriétés d’activité les plus utiles et décrit comment les utiliser dans le concepteur :

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Faux|Activité à exécuter lorsque la condition a la **valeur true**. Pour ajouter l' <xref:System.Activities.Statements.DoWhile.Body%2A> activité, déplacez une activité de la boîte à outils vers la zone **Body** sur le concepteur d’activités en **cours** avec le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Vrai|Condition à évaluer après chaque itération de la boucle. Pour définir le <xref:System.Activities.Statements.DoWhile.Condition%2A> , tapez une expression Visual Basic dans la zone **condition** sur le concepteur d’activités en **cours** ou dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi

- [While](../workflow-designer/while-activity-designer.md)
- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)