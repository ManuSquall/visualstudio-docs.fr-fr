---
title: Concepteur d’activités Concepteur de flux de travail-TryCatch
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TryCatch.UI
- System.Activities.Statements.Catch`1.UI
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b70f1d3174990ec12c621dff4a45ce4d899ceb4e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593068"
---
# <a name="trycatch-activity-designer"></a>Concepteur d'activités TryCatch

Le concepteur d’activités **TryCatch** permet de créer et de configurer une activité <xref:System.Activities.Statements.TryCatch>.

## <a name="the-trycatch-activity"></a>Activité TryCatch
 L’activité <xref:System.Activities.Statements.TryCatch> contient une activité de <xref:System.Activities.Statements.TryCatch.Try%2A>, une collection de **captures de\<TException >** et une activité <xref:System.Activities.Statements.TryCatch.Finally%2A>. Une <xref:System.Activities.Statements.Catch%601> de type **TException** contient un <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> et un <xref:System.Activities.Statements.Catch%601.Action%2A>. Ensemble, ils permettent d'implémenter un mécanisme classique de gestion des erreurs basé sur les exceptions. Une activité <xref:System.Activities.Statements.TryCatch> essaie d'exécuter son activité <xref:System.Activities.Statements.TryCatch.Try%2A>. Si l’activité <xref:System.Activities.Statements.TryCatch.Try%2A> lève une exception, l’activité <xref:System.Activities.Statements.TryCatch> utilise sa collection **Catch < TException\>** pour correspondre à l’exception. En cas de correspondance, la <xref:System.Activities.Statements.Catch%601.Action%2A> du **> Catch\<TException** correspondant est exécutée, servant de logique de gestion des erreurs pour l’exception. Si les activités de la section <xref:System.Activities.Statements.TryCatch.Try%2A> s'achèvent correctement ou les activités de <xref:System.Activities.Statements.TryCatch.Catches%2A> s'achèvent correctement, l'activité <xref:System.Activities.Statements.TryCatch> exécute son activité <xref:System.Activities.Statements.TryCatch.Finally%2A>. Pour plus d’informations, consultez [exceptions de Windows Workflow](/dotnet/framework/windows-workflow-foundation/exceptions).

### <a name="using-the-trycatch-activity-designer"></a>Utilisation du concepteur d'activités TryCatch

Accédez au concepteur d’activités **TryCatch** dans la catégorie **gestion des erreurs** de la **boîte à outils**.

Le concepteur d’activités **TryCatch** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. Cette opération crée une activité <xref:System.Activities.Statements.TryCatch> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut TryCatch. La valeur <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **TryCatch** ou dans la zone **DisplayName** de la grille des propriétés. Les autres propriétés doivent être modifiées sur la surface du concepteur d’activités **TryCatch** .

Cliquez sur le bouton de développement dans le coin supérieur droit de **TryCatch** Designer pour afficher les zones **try** **, catch et** **finally** dans la vue développée. Pour ajouter un catch, cliquez sur le bouton **Ajouter un nouveau catch** sur **TryCatch** designer. Le bouton se transforme en zone de liste déroulante Type. Sélectionnez un type d'exception et appuyez sur ENTRÉE pour ajouter le catch. Après l’ajout d’un **catch**, la zone catch se développe et une activité peut être déposée dans catch pour définir la logique d’exécution de la capture. Notez la présence d’une zone de texte à droite de la zone de catch développée. Vous pouvez nommer la variable d'exception à l'aide de cette zone de texte. La variable d’exception ne peut être utilisée que pour les activités au sein du même **catch**.

**TryCatch** designer ne prend pas en charge la modification des **catch**. Si vous souhaitez modifier le type d’exception, vous devez supprimer le **catch** et en ajouter un nouveau. Pour supprimer une **capture** , vous pouvez la sélectionner et la supprimer, ou sélectionner **supprimer** dans le menu contextuel accessible en cliquant avec le bouton droit.

### <a name="the-trycatch-properties"></a>Propriétés TryCatch

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.TryCatch>et décrit comment elles sont utilisées dans le concepteur.

|Nom de propriété|Obligatoire|Contrôle|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.TryCatch>. TryCatch est la valeur par défaut.|
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|Première activité exécutée lorsque <xref:System.Activities.Statements.TryCatch> s'exécute.|
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|Collection d’éléments **catch** à vérifier lorsque l’activité <xref:System.Activities.Statements.TryCatch.Try%2A> lève une exception.<br /><br /> Vous devez au moins ajouter une activité dans <xref:System.Activities.Statements.TryCatch.Catches%2A> ou une activité dans le bloc <xref:System.Activities.Statements.TryCatch.Finally%2A>.|
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|Activité à exécuter lorsque l'exécution de <xref:System.Activities.Statements.TryCatch.Try%2A> et de toutes les activités nécessaires de la collection <xref:System.Activities.Statements.TryCatch.Catches%2A> est terminée.<br /><br /> Vous devez au moins ajouter une activité dans <xref:System.Activities.Statements.TryCatch.Catches%2A> ou une activité dans le bloc <xref:System.Activities.Statements.TryCatch.Finally%2A>.|

## <a name="see-also"></a>Voir aussi

- [Regroupement](../workflow-designer/collection-activity-designers.md)
- [Rethrow](../workflow-designer/rethrow-activity-designer.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
