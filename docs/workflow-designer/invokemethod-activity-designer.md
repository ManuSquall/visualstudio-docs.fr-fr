---
title: Concepteur d’activités Concepteur de flux de travail-InvokeMethod
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8660cd82f9d671da3b535ac228e8ce62c875dc07
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593198"
---
# <a name="invokemethod-activity-designer"></a>Concepteur d'activités InvokeMethod

Le concepteur **InvokeMethod** est utilisé pour créer et configurer une activité <xref:System.Activities.Statements.InvokeMethod>.

## <a name="the-invokemethod-activity"></a>Activité InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> appelle une méthode publique d'un objet ou d'un type spécifié.

### <a name="use-the-invokemethod-activity-designer"></a>Utiliser le concepteur d’activités InvokeMethod

Accédez au concepteur d’activités **InvokeMethod** dans la catégorie **primitives** de la **boîte à outils**. Le concepteur d’activités **InvokeMethod** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, où les activités sont généralement placées, par exemple dans une <xref:System.Activities.Statements.Sequence>. La suppression du concepteur d’activités crée une activité <xref:System.Activities.Statements.InvokeMethod> avec un <xref:System.Activities.Activity.DisplayName%2A> par défaut de InvokeMethod. La <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l’en-tête du concepteur d’activités **InvokeMethod** ou dans la zone **DisplayName** de la grille des propriétés.

### <a name="the-invokemethod-properties"></a>Propriétés InvokeMethod

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.InvokeMethod> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés, et certaines d’entre elles peuvent être modifiées sur Concepteur de flux de travail surface.

|Nom de propriété|Obligatoire|Contrôle|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.InvokeMethod>. La valeur par défaut est InvokeMethod.<br /><br /> Bien que le <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est préférable d’en utiliser un.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|Nom de la méthode à appeler lorsque l'activité s'exécute. La méthode appelée doit être déclarée comme **publique**. Cette propriété peut être modifiée dans l’aire du concepteur et est obligatoire.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Collection de paramètres de la méthode appelée. Les paramètres doivent être ajoutés à la collection selon leur ordre d’affichage dans la signature de méthode. Pour afficher la boîte de dialogue **paramètres** dans laquelle vous pouvez définir cette propriété, cliquez sur le bouton de sélection dans le champ **paramètres** de la grille des propriétés. Cliquez sur le bouton **créer un argument** pour ajouter les paramètres.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Valeur de retour de l'appel de méthode.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Spécifie si la méthode est appelée de façon asynchrone. La valeur par défaut est **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Objet qui contient la méthode à appeler. Cette propriété peut être modifiée dans l'aire du concepteur.<br /><br /> La propriété <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> ou <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> doit obligatoirement être définie.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Type d'élément <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Cette propriété peut être modifiée dans l'aire du concepteur. Elle doit être définie uniquement si la méthode appelée est statique.|

Pour passer des paramètres en C# tant que paramètre de **sortie** (par exemple, `Method1(out myParam))`, utilisez l' **argument** InOutArgument à la place de

Les méthodes avec des arguments appelés **TargetObject** ou **result** ne peuvent pas être appelées à l’aide de l’activité <xref:System.Activities.Statements.InvokeMethod>. En effet, l'activité <xref:System.Activities.Statements.InvokeMethod> inscrit <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> et <xref:System.Activities.Statements.InvokeMethod.Result%2A> dans <xref:System.Activities.Activity.CacheMetadata%2A>.

L'algorithme permettant d'inscrire les paramètres dans <xref:System.Activities.Activity.CacheMetadata%2A> est présenté dans la liste suivante :

1. Inscrivez l'argument <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.

2. Inscrivez l'argument <xref:System.Activities.Statements.InvokeMethod.Result%2A>.

3. Effectuez une itération au sein de la collection <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> et inscrivez chaque argument.

L'exception obtenue est de type <xref:System.Activities.InvalidWorkflowException> avec le message suivant : 'InvokeMethod' : Une variable, un RuntimeArgument ou un DelegateArgument, portant le nom 'TargetObject' existe déjà. Les noms doivent être uniques au sein de la portée de l'environnement.

Cette restriction ne s’applique pas aux <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> et <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. Ils ne sont pas des arguments de flux de travail et ne sont donc pas inscrits dans la collection <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> de l’activité <xref:System.Activities.Statements.InvokeMethod> dans la méthode <xref:System.Activities.Activity.CacheMetadata%2A>.

## <a name="see-also"></a>Voir aussi

- [Primitifs](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
