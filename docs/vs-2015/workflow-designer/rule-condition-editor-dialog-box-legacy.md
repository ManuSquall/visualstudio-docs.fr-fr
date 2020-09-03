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
ms.openlocfilehash: 00df917b05f5073634b0956a0b44e5b0fc6026a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846329"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Éditeur de conditions de règle, boîte de dialogue (héritée)
Cette rubrique décrit comment utiliser la boîte de dialogue **éditeur de conditions de règle** dans le hérité [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Vous créez et modifiez des conditions de règle déclaratives à l’aide de la boîte de dialogue **éditeur de conditions de règle** . Ces conditions de règle sont exposées comme propriétés pour les activités prédéfinies Windows Workflow Foundation suivantes :

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

  Vous accédez à la boîte de dialogue **éditeur de conditions de règle** à l’aide de la boîte de [dialogue Sélectionner une condition (héritée)](../workflow-designer/select-condition-dialog-box-legacy.md).

  Le tableau suivant décrit les éléments d’interface utilisateur de la boîte de dialogue **éditeur de conditions de règle** .

|Élément de l’interface utilisateur|Description|
|----------------|-----------------|
|**Etat**|Entrez l'expression applicable à la condition de règle.|
|**OK**|Cliquez pour enregistrer la condition de règle.|

## <a name="entering-condition-expressions"></a>Entrée d'expressions de condition
 Les expressions de condition sont entrées sous forme de texte. Vous pouvez taper **cette.** dans l’éditeur pour référencer les champs, les propriétés et les méthodes utilisés dans le workflow, à l’aide d’un menu similaire à IntelliSense. Vous pouvez également taper directement un nom de membre de workflow. Vous pouvez ajouter des opérateurs logiques à la condition, tels que les opérateurs AND, OR ou NOT. Vous pouvez également ajouter des prédicats. Un prédicat se compose d’un opérateur binaire et de deux opérandes. Les opérateurs binaires pris en charge sont **==** ,, **>** **\<**, **>=** et **<=** . Les opérandes pris en charge sont à valeur de constante, à fonction arithmétique et à portée publique.

 Vous pouvez spécifier le type de comparaison, et vous pouvez comparer à une **valeur null** ou à une chaîne vide. Vous pouvez imbriquer des appels à des membres sur une variable qui contient un type complexe, par exemple `this.Address.State == "WA"`.

 L'éditeur de conditions de règle prend en charge les opérateurs suivants :

- Opérateurs relationnels: ==, =, !=

- Opérateurs de comparaison : <, \<=, > , >=

- Opérateurs arithmétiques: +, - , *, /, MOD

- Opérateurs logiques : AND,  && ou,  &#124;&#124;, NOT, !

- Opérateurs au niveau du bit : &, &#124;

  La priorité des opérateurs d'expression suit les règles de priorité des opérateurs C#.

  L'éditeur de conditions de règle prend en charge les opérateurs numériques suivants :

  this.i == 1D (la résolution est 1.0)

  this.i == 1E1 (la résolution est 10.0)

  this.i == 1L (la résolution est un entier long)

  this.i == 1M (la résolution est un nombre décimal)

  this.i == 1F (la résolution est un nombre unique)

  this.i == 1U (la résolution est un unsigned int)

  Pour plus d’informations sur les conditions, consultez [utilisation de conditions dans les workflows](https://msdn2.microsoft.com/library/bb628447.aspx).

## <a name="see-also"></a>Voir aussi
 [IfElseActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelseactivity.aspx) [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx) [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx) [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx) [boîte de dialogue Sélectionner la condition (héritée)](../workflow-designer/select-condition-dialog-box-legacy.md) [utilisation des conditions dans les workflows](https://msdn2.microsoft.com/library/bb628447.aspx) [Concepteur hérité pour Windows Workflow Foundation aide sur l’interface utilisateur](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)
