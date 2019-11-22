---
title: Éditeur de conditions de règle, boîte de dialogue (héritée) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a632b90e89e58c26ec72083fe3f4ed9223826dae
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302846"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Éditeur de conditions de règle, boîte de dialogue (héritée)
Cette rubrique décrit comment utiliser la boîte de dialogue **Éditeur de conditions de règle** dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Pour créer et modifier des conditions de règle déclaratives, utilisez la boîte de dialogue **Éditeur de conditions de règle**. Ces conditions de règle sont exposées comme propriétés pour les activités prédéfinies Windows Workflow Foundation suivantes :

- [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65045)

  Vous accédez à la boîte de dialogue **éditeur de conditions de règle** à l’aide de la boîte de [dialogue Sélectionner une condition (héritée)](../workflow-designer/select-condition-dialog-box-legacy.md).

  Le tableau suivant décrit les éléments d'interface utilisateur de la boîte de dialogue **Éditeur de conditions de règle**.

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**Etat**|Entrez l'expression applicable à la condition de règle.|
|**OK**|Cliquez pour enregistrer la condition de règle.|

## <a name="entering-condition-expressions"></a>Entrée d'expressions de condition
 Les expressions de condition sont entrées sous forme de texte. Vous pouvez taper **cette.** dans l’éditeur pour référencer les champs, les propriétés et les méthodes utilisés dans le workflow, à l’aide d’un menu similaire à IntelliSense. Vous pouvez également taper directement un nom de membre de workflow. Vous pouvez ajouter des opérateurs logiques à la condition, tels que les opérateurs AND, OR ou NOT. Vous pouvez également ajouter des prédicats. Un prédicat se compose d’un opérateur binaire et de deux opérandes. Les opérateurs binaires pris en charge sont **==** , **>** , **\<** , **>=** et **<=** . Les opérandes pris en charge sont à valeur de constante, à fonction arithmétique et à portée publique.

 Vous pouvez spécifier le type de comparaison, et vous pouvez comparer à une **valeur null** ou à une chaîne vide. Vous pouvez imbriquer des appels à des membres sur une variable qui contient un type complexe, par exemple `this.Address.State == "WA"`.

 L'éditeur de conditions de règle prend en charge les opérateurs suivants :

- Opérateurs relationnels: ==, =, !=

- Opérateurs de comparaison : <, \<=, >, > =

- Opérateurs arithmétiques: +, - , *, /, MOD

- Opérateurs logiques : and, & &, or &#124; &#124;, not, !

- Opérateurs au niveau du bit : &,&#124;

  La priorité des opérateurs d'expression suit les règles de priorité des opérateurs C#.

  L'éditeur de conditions de règle prend en charge les opérateurs numériques suivants :

  this.i == 1D (la résolution est 1.0)

  this.i == 1E1 (la résolution est 10.0)

  this.i == 1L (la résolution est un entier long)

  this.i == 1M (la résolution est un nombre décimal)

  this.i == 1F (la résolution est un nombre unique)

  this.i == 1U (la résolution est un unsigned int)

  Pour plus d’informations sur les conditions, consultez [utilisation de conditions dans les workflows](https://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>Voir aussi
 [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033) [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039) [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049) [boîte de dialogue Sélectionner la condition (héritée)](../workflow-designer/select-condition-dialog-box-legacy.md) [utilisation des conditions dans les workflows](https://go.microsoft.com/fwlink?LinkID=65009) [Concepteur hérité pour Windows Workflow Foundation aide sur l’interface utilisateur](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)