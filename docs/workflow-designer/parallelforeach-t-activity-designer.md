---
title: Concepteur d’activités Concepteur de flux de travail-ParallelForEach &lt;T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b68cd543ed41408e7510708367c8e539c0702ea1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650088"
---
# <a name="parallelforeach-activity-designer"></a>Concepteur d’activités ParallelForEach

L’activité <xref:System.Activities.Statements.ParallelForEach%601> énumère les éléments d’une collection et, pour chacun d’eux, exécute en parallèle une instruction incorporée, qui se trouve de façon asynchrone sur le même thread. Utilisez cette activité de contrôle de flux au lieu de l'activité <xref:System.Activities.Statements.Sequence> si ses activités enfants sont censées devenir inactives.

L’activité <xref:System.Activities.Statements.ParallelForEach%601> a une propriété <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> qui contient une expression d’Visual Basic spécifiée par l’utilisateur. L’activité <xref:System.Activities.Statements.ParallelForEach%601> évalue cette propriété après l’exécution de chaque branche. Si elle prend la **valeur true**, l’activité de <xref:System.Activities.Statements.ParallelForEach%601> se termine sans exécuter les autres branches. Si la <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> n’a pas la **valeur true**, l’activité de <xref:System.Activities.Statements.ParallelForEach%601> se termine lorsque toutes ses activités enfants sont terminées.

## <a name="the-parallelforeacht-activity"></a>L’activité ParallelForEach < T \>

L'activité <xref:System.Activities.Statements.ParallelForEach%601> énumère ses valeurs et planifie la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> pour chaque valeur énumérée. Elle planifie seulement la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. La manière dont le corps s'exécute dépend de l'inactivation de la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>.

Si la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> ne devient pas inactive, son exécution s'effectue dans l'ordre inverse, car les activités planifiées sont gérées comme une pile, la dernière activité planifiée s'exécutant en premier. Par exemple, si vous avez une collection de {1,2,3,4}in <xref:System.Activities.Statements.ParallelForEach%601> et utilisez un **WriteLine** comme corps pour écrire la valeur. Vous avez 4, 3, 2, 1 imprimée dans la console. Cela est dû au fait que **WriteLine** n’est pas inactif, de sorte que les activités **WriteLine** ont été planifiées, après l’exécution d’un comportement de pile (premier en dernier sorti).

Par contre, si des activités dans la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> peuvent devenir inactives, par exemple une activité <xref:System.ServiceModel.Activities.Receive> ou <xref:System.Activities.Statements.Delay>, Il n'est pas nécessaire d'attendre qu'elles soient terminées. <xref:System.Activities.Statements.ParallelForEach%601> accède à l'activité de corps planifiée suivante et l'exécute. Si cette activité devient inactive à son tour, <xref:System.Activities.Statements.ParallelForEach%601> passe de nouveau à l'activité de corps suivante.

### <a name="using-the-parallelforeacht-activity-designer"></a>Utilisation du concepteur d’activités ParallelForEach \<T >

Accédez au concepteur d’activités **ParallelForEach \<T >** dans la catégorie **Flow Control** de la **boîte à outils**.

Le concepteur d’activités **ParallelForEach \<T >** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les concepteurs d’activités sont généralement placés, par exemple, dans une activité **Sequence** définition. Après la suppression dans le Concepteur de flux de travail, il crée une activité <xref:System.Activities.Statements.ParallelForEach%601>, qui, par défaut, contient une <xref:System.Activities.Activity.DisplayName%2A> de **ParallelForEach < Int32 \>.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>Propriétés de ParallelForEach < T \> dans le Concepteur de flux de travail

Le tableau suivant répertorie les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.ParallelForEach%601> et décrit comment elles sont utilisées dans le concepteur.

|Nom de propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom d'affichage convivial du concepteur d'activités dans l'en-tête. La valeur par défaut est **ParallelForEach \<Int32 >** . La valeur peut éventuellement être modifiée dans la grille des **Propriétés** ou directement dans l’en-tête du concepteur d’activités.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Activité à exécuter pour chaque élément dans la collection. Pour ajouter l’activité <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>, déposez une activité de la boîte à outils dans la zone **corps** de l' **\<T ParallelForEach >** concepteur d’activités avec le texte d’indication « déposer l’activité ici ».|
|**TypeArgument**|True|Type des éléments dans la collection <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> spécifiée par le paramètre générique *t*. Par défaut, **TypeArgument** a la valeur **Int32**. Pour modifier le type T dans le concepteur d’activités **ParallelForEach < T \>** , modifiez la valeur de la zone de liste déroulante **TypeArgument** dans la grille des propriétés.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|Collection d’éléments à itérer. Pour définir la <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, tapez une expression Visual Basic dans la zone **valeurs** du concepteur d’activités **ForEach < t \>** dans la zone avec le texte d’indication « entrer une expression vb » ou dans la zone **valeurs** de la fenêtre **Propriétés** .|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Propriété évaluée à l'issue de chaque itération. Si sa valeur est True, les itérations en attente planifiées sont annulées. Si cette propriété n'est pas définie, toutes les instructions planifiées s'exécutent jusqu'à ce qu'elles soient terminées.|

Par défaut, l'itérateur de boucle est nommé « item ». Vous pouvez modifier le nom de la variable d’itérateur dans la zone **foreach** dans **ParallelForEach \<T >** concepteur d’activités. L'itérateur de boucle peut être utilisé dans des expressions dans les enfants de l'activité <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>Voir aussi

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)