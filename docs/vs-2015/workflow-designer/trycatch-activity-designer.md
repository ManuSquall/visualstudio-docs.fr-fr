---
title: Concepteur d’activités TryCatch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b26bb37d1ddeabb77b1399c6cbce5ae55b59702c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654664"
---
# <a name="trycatch-activity-designer"></a>Concepteur d'activités TryCatch
Le concepteur d’activités **TryCatch** permet de créer et de configurer une <xref:System.Activities.Statements.TryCatch> activité.

## <a name="the-trycatch-activity"></a>Activité TryCatch
 L' <xref:System.Activities.Statements.TryCatch> activité contient une <xref:System.Activities.Statements.TryCatch.Try%2A> activité, une collection de **captures \<TException> ** et une <xref:System.Activities.Statements.TryCatch.Finally%2A> activité. Un <xref:System.Activities.Statements.Catch%601> de type **TException** contient un <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> et un <xref:System.Activities.Statements.Catch%601.Action%2A> . Ensemble, ils permettent d'implémenter un mécanisme classique de gestion des erreurs basé sur les exceptions. Une activité <xref:System.Activities.Statements.TryCatch> essaie d'exécuter son activité <xref:System.Activities.Statements.TryCatch.Try%2A>. Si l' <xref:System.Activities.Statements.TryCatch.Try%2A> activité lève une exception, l' <xref:System.Activities.Statements.TryCatch> activité utilise sa collection **catch<TException \> ** pour correspondre à l’exception. En cas de correspondance, le <xref:System.Activities.Statements.Catch%601.Action%2A> de la **capture interceptée \<TException> ** correspondante est exécuté, servant de logique de gestion des erreurs pour l’exception. Si les activités de la section <xref:System.Activities.Statements.TryCatch.Try%2A> s'achèvent correctement ou les activités de <xref:System.Activities.Statements.TryCatch.Catches%2A> s'achèvent correctement, l'activité <xref:System.Activities.Statements.TryCatch> exécute son activité <xref:System.Activities.Statements.TryCatch.Finally%2A>. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Exceptions](https://msdn.microsoft.com/library/065205cc-52dd-4f30-9578-b17d8d113136).

### <a name="using-the-trycatch-activity-designer"></a>Utilisation du concepteur d'activités TryCatch
 Le concepteur d’activités **TryCatch** se trouve dans la catégorie **gestion des erreurs** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** sur le côté gauche de [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou en sélectionnant **barre d’outils** dans le menu **affichage** , ou encore en Ctrl + Alt + X).

 Le concepteur d’activités **TryCatch** peut être déplacé de la **boîte à outils** et déposé dans l’aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)] , là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . Cette opération crée une activité <xref:System.Activities.Statements.TryCatch> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut TryCatch. La <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête du concepteur d’activités **TryCatch** ou dans la zone **DisplayName** de la grille des propriétés. Les autres propriétés doivent être modifiées sur la surface du concepteur d’activités **TryCatch** .

 Cliquez sur le bouton de développement dans le coin supérieur droit de **TryCatch** Designer pour afficher les zones **try** **, catch et** **finally** dans la vue développée. Pour ajouter un catch, cliquez sur le bouton **Ajouter un nouveau catch** sur **TryCatch** designer. Le bouton se transforme en zone de liste déroulante Type. Sélectionnez un type d'exception et appuyez sur ENTRÉE pour ajouter le catch. Après l’ajout d’un **catch**, la zone catch se développe et une activité peut être déposée dans catch pour définir la logique d’exécution de la capture. Notez la présence d’une zone de texte à droite de la zone de catch développée. Vous pouvez nommer la variable d'exception à l'aide de cette zone de texte. La variable d’exception ne peut être utilisée que pour les activités au sein du même **catch**.

 **TryCatch** designer ne prend pas en charge la modification des **catch**. Si vous souhaitez modifier le type d’exception, vous devez supprimer le **catch** et en ajouter un nouveau. Pour supprimer une **capture** , vous pouvez la sélectionner et la supprimer, ou utiliser le menu **supprimer** du menu contextuel accessible en cliquant avec le bouton droit.

### <a name="the-trycatch-properties"></a>Propriétés TryCatch
 Le tableau suivant présente les <xref:System.Activities.Statements.TryCatch> Propriétés et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Faux|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.TryCatch>. TryCatch est la valeur par défaut.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|Faux|Première activité exécutée lorsque <xref:System.Activities.Statements.TryCatch> s'exécute.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|Faux|Collection d’éléments **catch** à vérifier lorsque l' <xref:System.Activities.Statements.TryCatch.Try%2A> activité lève une exception.<br /><br /> Vous devez au moins ajouter une activité dans <xref:System.Activities.Statements.TryCatch.Catches%2A> ou une activité dans le bloc <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|Faux|Activité à exécuter lorsque l'exécution de <xref:System.Activities.Statements.TryCatch.Try%2A> et de toutes les activités nécessaires de la collection <xref:System.Activities.Statements.TryCatch.Catches%2A> est terminée.<br /><br /> Vous devez au moins ajouter une activité dans <xref:System.Activities.Statements.TryCatch.Catches%2A> ou une activité dans le bloc <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>Voir aussi
 [Levée de nouvelle](../workflow-designer/throw-activity-designer.md) [levée](../workflow-designer/rethrow-activity-designer.md) de [collection](../workflow-designer/collection-activity-designers.md)