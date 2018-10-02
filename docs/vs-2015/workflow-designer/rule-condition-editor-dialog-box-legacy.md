---
title: Boîte de dialogue de l’éditeur de conditions de règle (hérité) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 7c78f17c74063e68c1ab5be6e79c61ccf6f39610
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494913"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>Éditeur de conditions de règle, boîte de dialogue (héritée)
Cette rubrique décrit comment utiliser le **éditeur de conditions de règle** boîte de dialogue dans les anciennes [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Créer et de modifier les conditions de règle déclarative à l’aide de la **éditeur de conditions de règle** boîte de dialogue. Ces conditions de règle sont exposées comme propriétés pour les activités prédéfinies Windows Workflow Foundation suivantes :  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
 Vous accédez à la **éditeur de conditions de règle** boîte de dialogue à l’aide de la [sélectionner une boîte de dialogue Condition (hérité)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **éditeur de conditions de règle** boîte de dialogue.  
  
|Élément d'interface utilisateur|Description|  
|----------------|-----------------|  
|**Condition :**|Entrez l'expression applicable à la condition de règle.|  
|**OK**|Cliquez pour enregistrer la condition de règle.|  
  
## <a name="entering-condition-expressions"></a>Entrée d'expressions de condition  
 Les expressions de condition sont entrées sous forme de texte. Vous pouvez taper **cela.** dans l’éditeur pour référencer des champs, propriétés et méthodes utilisées dans le flux de travail, à l’aide un menu de type IntelliSense. Vous pouvez également taper directement un nom de membre de workflow. Vous pouvez ajouter des opérateurs logiques à la condition, tels que les opérateurs AND, OR ou NOT. Vous pouvez également ajouter des prédicats. Un prédicat se compose d’un opérateur binaire et de deux opérandes. Les opérateurs binaires pris en charge sont **==**, **>**, **\<**, **>=**, et **<=**. Les opérandes pris en charge sont à valeur de constante, à fonction arithmétique et à portée publique.  
  
 Vous pouvez spécifier le type de comparaison, et vous pouvez comparer aux **null** ou une chaîne vide. Vous pouvez imbriquer des appels à des membres sur une variable qui contient un type complexe, par exemple `this.Address.State == "WA"`.  
  
 L'éditeur de conditions de règle prend en charge les opérateurs suivants :  
  
-   Opérateurs relationnels: ==, =, !=  
  
-   Opérateurs de comparaison : <, \<=, >, > =  
  
-   Opérateurs arithmétiques: +, - , *, /, MOD  
  
-   Opérateurs logiques : et, & &, OR, &#124; &#124;, NOT, !  
  
-   Opérateurs au niveau du bit : &,&#124;  
  
 La priorité des opérateurs d'expression suit les règles de priorité des opérateurs C#.  
  
 L'éditeur de conditions de règle prend en charge les opérateurs numériques suivants :  
  
 this.i == 1D (la résolution est 1.0)  
  
 this.i == 1E1 (la résolution est 10.0)  
  
 this.i == 1L (la résolution est un entier long)  
  
 this.i == 1M (la résolution est un nombre décimal)  
  
 this.i == 1F (la résolution est un nombre unique)  
  
 this.i == 1U (la résolution est un unsigned int)  
  
 Pour plus d’informations sur les conditions, consultez [à l’aide de Conditions dans les Workflows](http://go.microsoft.com/fwlink?LinkID=65009).  
  
## <a name="see-also"></a>Voir aussi  
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [Sélectionnez la Condition, boîte de dialogue (hérité)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Utilisation de Conditions dans les Workflows](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Aide de l’interface utilisateur du concepteur hérité pour Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)