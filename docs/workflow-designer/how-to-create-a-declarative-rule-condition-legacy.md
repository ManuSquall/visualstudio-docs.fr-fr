---
title: "Proc&#233;dure&#160;: cr&#233;er une condition de r&#232;gle d&#233;clarative (h&#233;rit&#233;e) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "instructions conditionnelles, conditions de règle déclaratives"
  - "conditions de règle déclaratives"
  - "Éditeur de conditions de règle (boîte de dialogue)"
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Proc&#233;dure&#160;: cr&#233;er une condition de r&#232;gle d&#233;clarative (h&#233;rit&#233;e)
Cette rubrique décrit comment déclarer une condition de règle à l'aide du [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Une instruction de condition prend la valeur **True** ou **False**.Une condition de règle déclarative est une instruction de condition créée à l'aide de la [Éditeur de conditions de règle, boîte de dialogue \(héritée\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) et conservée en tant que fichier XML avec le workflow.Elle peut inclure des prédicats qui comparent l'état du workflow et l'algèbre booléen qui associe plusieurs prédicats.  
  
 Les conditions de règle déclaratives sont utilisées dans les activités Windows Workflow Foundation prédéfinies suivantes :  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### Pour créer une condition de règle déclarative à l'aide de l'Éditeur de conditions de règle  
  
1.  Dans la fenêtre **Propriétés** de l'activité, cliquez sur la propriété **Condition** ou sur la propriété **UntilCondition**, selon l'activité.  
  
2.  Sélectionnez **Condition de règle déclarative** dans la liste, pour cette propriété.  
  
3.  Développez la propriété **Condition** ou la propriété **UntilCondition**.  
  
4.  Cliquez sur la propriété **ConditionName**.  
  
5.  Cliquez sur les boutons de sélection de la propriété **ConditionName** \(**\[.\]**\) pour ouvrir la boîte de dialogue **Sélectionner la condition**.  
  
6.  Cliquez sur **Nouvelle condition** pour ouvrir la boîte de dialogue **Éditeur de conditions de règle**.  
  
7.  Tapez l'expression de la condition dans la zone de texte **Condition**.  
  
     Pour plus d'informations sur la création d'expressions de condition, consultez [Éditeur de conditions de règle, boîte de dialogue \(héritée\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  Une fois que vous avez terminé la création de l'expression conditionnelle, cliquez sur **OK** pour fermer la boîte de dialogue et créer la condition de règle avec affectation de nom.  
  
     La boîte de dialogue **Sélectionner la condition** s'ouvre.  
  
     Pour plus d'informations sur l'utilisation de la boîte de dialogue **Sélectionner la condition**, consultez [Sélectionner la condition, boîte de dialogue \(héritée\)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## Voir aussi  
 [Activités de workflow héritées](../workflow-designer/legacy-workflow-activities.md)   
 [Utilisation de ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Utilisation de l'activité IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Utilisation de l'activité Replicator](http://go.microsoft.com/fwlink?LinkID=65080)   
 [Utilisation de l'activité While](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Éditeur de conditions de règle, boîte de dialogue \(héritée\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Sélectionner la condition, boîte de dialogue \(héritée\)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Utilisation de conditions dans les workflows](http://go.microsoft.com/fwlink?LinkID=65009)