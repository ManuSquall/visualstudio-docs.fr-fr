---
title: Concepteur d’activités en cours | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b63c3e2e0907bcaf13ada4cbb20ce5527a240fe3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656769"
---
# <a name="dowhile-activity-designer"></a>Concepteur d'activités DoWhile
L' <xref:System.Activities.Statements.DoWhile> activité exécute l’activité contenue dans son <xref:System.Activities.Statements.DoWhile.Body%2A> au moins une fois, jusqu’à ce qu’une condition spécifiée ait la **valeur false**. Si vous devez exécuter zéro ou plusieurs fois l'activité contenue dans le corps d'une boucle, utilisez plutôt l'activité <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Propriétés de DoWhile dans Workflow Designer
 Le tableau suivant affiche les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.DoWhile> et décrit comment les utiliser dans le concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Faux|Activité à exécuter lorsque la condition a la **valeur true**. Pour ajouter l' <xref:System.Activities.Statements.DoWhile.Body%2A> activité, déplacez une activité de la boîte à outils vers la zone **Body** sur le concepteur d’activités en **cours** avec le texte d’indication « déposer l’activité ici ».|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Vrai|Condition à évaluer après chaque itération de la boucle. Pour définir le <xref:System.Activities.Statements.DoWhile.Condition%2A> , tapez une [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] expression dans la zone **condition** sur le concepteur d’activités en **cours** ou dans la grille des propriétés.|

## <a name="see-also"></a>Voir aussi
 [Pendant](../workflow-designer/while-activity-designer.md) [le contrôle du workflow](../workflow-designer/control-flow-activity-designers.md)