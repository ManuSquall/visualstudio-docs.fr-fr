---
title: "&#201;diteur de conditions de r&#232;gle, bo&#238;te de dialogue (h&#233;rit&#233;e) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI"
helpviewer_keywords: 
  - "Éditeur de conditions de règle (boîte de dialogue)"
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &#201;diteur de conditions de r&#232;gle, bo&#238;te de dialogue (h&#233;rit&#233;e)
Cette rubrique décrit comment utiliser la boîte de dialogue **Éditeur de conditions de règle** dans le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité.Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Pour créer et modifier des conditions de règle déclaratives, utilisez la boîte de dialogue **Éditeur de conditions de règle**.Ces conditions de règle sont exposées comme propriétés pour les activités prédéfinies Windows Workflow Foundation suivantes :  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
 Vous accédez à la boîte de dialogue **Éditeur de conditions de règle** en utilisant le [Sélectionner la condition, boîte de dialogue \(héritée\)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
 Le tableau suivant décrit les éléments d'interface utilisateur de la boîte de dialogue **Éditeur de conditions de règle**.  
  
|Élément d'interface|Description|  
|-------------------------|-----------------|  
|**Condition :**|Entrez l'expression applicable à la condition de règle.|  
|**OK**|Cliquez pour enregistrer la condition de règle.|  
  
## Entrée d'expressions de condition  
 Les expressions de condition sont entrées sous forme de texte.Vous pouvez taper **this.** dans l'éditeur pour référencer les champs, les propriétés et les méthodes utilisés dans le workflow, à l'aide d'un type\-de menu IntelliSense.Vous pouvez également taper directement un nom de membre de workflow.Vous pouvez ajouter des opérateurs logiques à la condition, tels que les opérateurs AND, OR ou NOT.Vous pouvez également ajouter des prédicats.Un prédicat se compose d'un opérateur binaire et de deux opérandes.Les opérateurs binaires pris en charge sont les suivants : **\=\=**, **\>**, **\<**, **\>\=** et **\<\=**.Les opérandes pris en charge sont à valeur de constante, à fonction arithmétique et à portée publique.  
  
 Vous pouvez spécifier le type de comparaison et comparer à la valeur **null** ou à une chaîne vide.Vous pouvez imbriquer des appels à des membres sur une variable qui contient un type complexe, par exemple `this.Address.State == "WA"`.  
  
 L'éditeur de conditions de règle prend en charge les opérateurs suivants :  
  
-   Opérateurs relationnels: \=\=, \=, \!\=  
  
-   Opérateurs de comparaison : \<, \<\=, \>, \>\=  
  
-   Opérateurs arithmétiques: \+, \- , \*, \/, MOD  
  
-   Opérateurs logiques : AND, &&, OR, &#124;&#124;, NOT, \!  
  
-   Opérateurs de bits : &, &#124;  
  
 La priorité des opérateurs d'expression suit les règles de priorité des opérateurs C\#.  
  
 L'éditeur de conditions de règle prend en charge les opérateurs numériques suivants :  
  
 this.i \=\= 1D \(la résolution est 1.0\)  
  
 this.i \=\= 1E1 \(la résolution est 10.0\)  
  
 this.i \=\= 1L \(la résolution est un entier long\)  
  
 this.i \=\= 1M \(la résolution est un nombre décimal\)  
  
 this.i \=\= 1F \(la résolution est un nombre unique\)  
  
 this.i \=\= 1U \(la résolution est un unsigned int\)  
  
 Pour plus d'informations sur les conditions, consultez [Utilisation de conditions dans les workflows](http://go.microsoft.com/fwlink?LinkID=65009) \(page pouvant être en anglais\).  
  
## Voir aussi  
 [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)   
 [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)   
 [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)   
 [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)   
 [Sélectionner la condition, boîte de dialogue \(héritée\)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Utilisation de conditions dans les workflows](http://go.microsoft.com/fwlink?LinkID=65009)   
 [Aide de l'interface utilisateur du concepteur hérité pour Windows Workflow Foundation](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)