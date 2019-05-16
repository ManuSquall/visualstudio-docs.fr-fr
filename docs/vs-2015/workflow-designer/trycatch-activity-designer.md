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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fb155cc7bbf4efbda54666f91f2db3f92e6c378c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697077"
---
# <a name="trycatch-activity-designer"></a>Concepteur d'activités TryCatch
Le **TryCatch** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.TryCatch> activité.  
  
## <a name="the-trycatch-activity"></a>Activité TryCatch  
 Le <xref:System.Activities.Statements.TryCatch> activité contient un <xref:System.Activities.Statements.TryCatch.Try%2A> activité, une collection de **Catch\<TException >** et un <xref:System.Activities.Statements.TryCatch.Finally%2A> activité. Un <xref:System.Activities.Statements.Catch%601> de type **TException** contient un <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> et un <xref:System.Activities.Statements.Catch%601.Action%2A>. Ensemble, ils permettent d'implémenter un mécanisme classique de gestion des erreurs basé sur les exceptions. Une activité <xref:System.Activities.Statements.TryCatch> essaie d'exécuter son activité <xref:System.Activities.Statements.TryCatch.Try%2A>. Si le <xref:System.Activities.Statements.TryCatch.Try%2A> activité lève une exception, le <xref:System.Activities.Statements.TryCatch> activité utilise son **intercepter < TException\>**  collection pour correspondre à l’exception. S’il existe une correspondance, puis le <xref:System.Activities.Statements.Catch%601.Action%2A> correspondantes **Catch\<TException >** est exécutée, servant à la gestion logique pour l’exception d’erreur. Si les activités de la section <xref:System.Activities.Statements.TryCatch.Try%2A> s'achèvent correctement ou les activités de <xref:System.Activities.Statements.TryCatch.Catches%2A> s'achèvent correctement, l'activité <xref:System.Activities.Statements.TryCatch> exécute son activité <xref:System.Activities.Statements.TryCatch.Finally%2A>. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Exceptions](https://msdn.microsoft.com/library/065205cc-52dd-4f30-9578-b17d8d113136).  
  
### <a name="using-the-trycatch-activity-designer"></a>Utilisation du concepteur d'activités TryCatch  
 Le **TryCatch** Concepteur d’activités peut être trouvé dans le **gestion des erreurs** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils** onglet sur le côté gauche de la [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTLR + ALT + X.)  
  
 Le **TryCatch** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette opération crée une activité <xref:System.Activities.Statements.TryCatch> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut TryCatch. Le <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête de la **TryCatch** Concepteur d’activités ou dans le **DisplayName** case de la grille des propriétés. Les autres propriétés doivent être modifiées sur la surface de la **TryCatch** Concepteur d’activités.  
  
 Cliquez sur le bouton développer dans le coin supérieur droit de **TryCatch** concepteur pour afficher la **essayez**, **intercepte**, et **enfin** zones dans le vue développée. Pour ajouter un bloc catch, cliquez sur le **ajouter un nouveau catch** bouton sur **TryCatch** concepteur. Le bouton se transforme en zone de liste déroulante Type. Sélectionnez un type d'exception et appuyez sur ENTRÉE pour ajouter le catch. Après avoir ajouté un **Catch**, la zone de catch se développe et une activité peut être déposée dans le bloc catch pour définir la logique d’exécution de l’interception. Notez la présence d’une zone de texte à droite de la zone de catch développée. Vous pouvez nommer la variable d'exception à l'aide de cette zone de texte. La variable d’exception peut uniquement être utilisée pour les activités au sein du même **Catch**.  
  
 Le **TryCatch** concepteur ne prend pas en charge la modification **Catch**. Si vous souhaitez modifier le type d’exception, vous devez supprimer le **Catch** et ajouter un nouveau. Un **Catch** peut être supprimé en sélectionnant et en la supprimant ou en utilisant le **supprimer** menu sur le menu contextuel accédé par clic droit.  
  
### <a name="the-trycatch-properties"></a>Propriétés TryCatch  
 Le tableau suivant présente le <xref:System.Activities.Statements.TryCatch>propriétés et décrit comment elles sont utilisées dans le concepteur.  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.TryCatch>. TryCatch est la valeur par défaut.|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Première activité exécutée lorsque <xref:System.Activities.Statements.TryCatch> s'exécute.|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|La collection de **Catch** éléments à vérifier lorsque le <xref:System.Activities.Statements.TryCatch.Try%2A> activité lève une exception.<br /><br /> Vous devez au moins ajouter une activité dans <xref:System.Activities.Statements.TryCatch.Catches%2A> ou une activité dans le bloc <xref:System.Activities.Statements.TryCatch.Finally%2A>.|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Activité à exécuter lorsque l'exécution de <xref:System.Activities.Statements.TryCatch.Try%2A> et de toutes les activités nécessaires de la collection <xref:System.Activities.Statements.TryCatch.Catches%2A> est terminée.<br /><br /> Vous devez au moins ajouter une activité dans <xref:System.Activities.Statements.TryCatch.Catches%2A> ou une activité dans le bloc <xref:System.Activities.Statements.TryCatch.Finally%2A>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Collection](../workflow-designer/collection-activity-designers.md)   
 [rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)