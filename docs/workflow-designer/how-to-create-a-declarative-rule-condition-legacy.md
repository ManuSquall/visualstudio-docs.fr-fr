---
title: 'Comment : créer une Condition de règle déclarative (héritée) | Documents Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e8b1d1220f11d27ee193e3e82168f4c10558d86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Procédure : créer une condition de règle déclarative (héritée)
Cette rubrique décrit comment déclarer une condition de règle à l’aide de Windows Workflow Designer hérité qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Une instruction de condition prend la valeur de **True** ou **False**. Une condition de règle déclarative est une instruction de condition qui est créée à l’aide de la [boîte de dialogue Éditeur de règle de Condition (hérité)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) et stockés au format XML avec le flux de travail. Elle peut inclure des prédicats qui comparent l’état du workflow et l’algèbre booléen qui associe plusieurs prédicats.

 Les conditions de règle déclaratives sont utilisées dans les activités Windows Workflow Foundation prédéfinies suivantes :

-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

-   [Activité WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Pour créer une condition de règle déclarative à l'aide de l'Éditeur de conditions de règle

1.  Dans l’activité **propriétés** fenêtre, cliquez sur le **Condition** propriété ou **UntilCondition** propriété, en fonction de l’activité.

2.  Sélectionnez **Condition de règle déclarative** dans la liste pour la propriété.

3.  Développez le **Condition** ou **UntilCondition** propriété.

4.  Cliquez sur le **ConditionName** propriété.

5.  Cliquez sur le **ConditionName** points de suspension **[...]**  pour ouvrir le **sélectionner la Condition** boîte de dialogue.

6.  Cliquez sur **nouvelle Condition** pour ouvrir le **éditeur de conditions de règle** boîte de dialogue.

7.  Tapez l’expression de la condition dans la **Condition** zone de texte.

     Pour plus d’informations sur la façon de créer des expressions de condition, consultez [boîte de dialogue Éditeur de règle de Condition (hérité)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8.  Lorsque vous avez terminé la création de l’expression de condition, cliquez sur **OK** pour fermer la boîte de dialogue et créer la condition de règle avec affectation de nom.

     Le **sélectionner la Condition** boîte de dialogue s’ouvre.

     Pour plus d’informations sur l’utilisation de la **sélectionner la Condition** boîte de dialogue, consultez [sélectionner une boîte de dialogue Condition (hérité)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Voir aussi

- [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)
- [À l’aide de ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)
- [Utilisation de l’activité IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65075)
- [Utilisation de l’activité Replicator](http://go.microsoft.com/fwlink?LinkID=65080)
- [À l’aide en activité](http://go.microsoft.com/fwlink?LinkID=65091)
- [Éditeur de conditions de règle, boîte de dialogue (hérité)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)
- [Sélectionner la condition, boîte de dialogue (hérité)](../workflow-designer/select-condition-dialog-box-legacy.md)
- [À l’aide de Conditions dans les Workflows](http://go.microsoft.com/fwlink?LinkID=65009)