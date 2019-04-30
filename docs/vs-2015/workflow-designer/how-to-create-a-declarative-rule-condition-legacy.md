---
title: 'Procédure : Créer une Condition de règle déclarative (hérité) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dbdcc268b71f2926307b500126840391dd5308fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931246"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Procédure : Créer une condition de règle déclarative (héritée)
Cette rubrique décrit comment déclarer une condition de règle à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Une instruction de condition prend la valeur **True** ou **False**. Une condition de règle déclarative est une instruction de condition qui est créée à l’aide de la [boîte de dialogue Éditeur de Condition de règle (hérité)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) et stockées au format XML avec le flux de travail. Elle peut inclure des prédicats qui comparent l'état du workflow et l'algèbre booléen qui associe plusieurs prédicats.  
  
 Les conditions de règle déclaratives sont utilisées dans les activités Windows Workflow Foundation prédéfinies suivantes :  
  
- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Pour créer une condition de règle déclarative à l'aide de l'Éditeur de conditions de règle  
  
1. Dans l’activité **propriétés** fenêtre, cliquez sur le **Condition** propriété ou **UntilCondition** propriété, en fonction de l’activité.  
  
2. Sélectionnez **Condition de règle déclarative** dans la liste pour la propriété.  
  
3. Développez le **Condition** ou **UntilCondition** propriété.  
  
4. Cliquez sur le **ConditionName** propriété.  
  
5. Cliquez sur le **ConditionName** ellipses **[...]**  pour ouvrir le **sélectionner la Condition** boîte de dialogue.  
  
6. Cliquez sur **nouvelle Condition** pour ouvrir le **éditeur de conditions de règle** boîte de dialogue.  
  
7. Tapez l’expression pour la condition dans le **Condition** zone de texte.  
  
     Pour plus d’informations sur la création d’expressions de condition, consultez [boîte de dialogue Éditeur de Condition de règle (hérité)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8. Lorsque vous avez terminé de créer l’expression de condition, cliquez sur **OK** pour fermer la boîte de dialogue et créer la condition de règle avec affectation de nom.  
  
     Le **sélectionner la Condition** boîte de dialogue s’ouvre.  
  
     Pour plus d’informations sur la façon d’utiliser le **sélectionner la Condition** boîte de dialogue, consultez [sélectionner une boîte de dialogue Condition (hérité)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Activités de flux de travail hérité](../workflow-designer/legacy-workflow-activities.md)   
 [Utilisation de ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [À l’aide de l’activité IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)   
 [À l’aide de l’activité Replicator](http://go.microsoft.com/fwlink?LinkID=65080)   
 [À l’aide de le pendant qu’activité](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Boîte de dialogue de l’éditeur de conditions de règle (hérité)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Sélectionnez la Condition, boîte de dialogue (hérité)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Utilisation de Conditions dans les Workflows](http://go.microsoft.com/fwlink?LinkID=65009)