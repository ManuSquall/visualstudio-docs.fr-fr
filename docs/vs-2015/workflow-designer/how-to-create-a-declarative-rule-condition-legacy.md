---
title: 'Comment : créer une condition de règle déclarative (héritée) | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c23fed64d7f3a7681fce96663262f6d633299a9
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849338"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Procédure : créer une condition de règle déclarative (héritée)
Cette rubrique décrit comment déclarer une condition de règle à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Une instruction de condition prend la **valeur true** ou **false**. Une condition de règle déclarative est une instruction de condition créée à l’aide de la [boîte de dialogue Éditeur de conditions de règle (héritée)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) et stockée en tant que XML avec le flux de travail. Elle peut inclure des prédicats qui comparent l'état du workflow et l'algèbre booléen qui associe plusieurs prédicats.

 Les conditions de règle déclaratives sont utilisées dans les activités Windows Workflow Foundation prédéfinies suivantes :

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [ReplicatorActivity](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>Pour créer une condition de règle déclarative à l'aide de l'Éditeur de conditions de règle

1. Dans la fenêtre **Propriétés** de l’activité, cliquez sur la propriété **condition** ou sur la propriété **UntilCondition** , en fonction de l’activité.

2. Sélectionnez **condition de règle déclarative** dans la liste pour la propriété.

3. Développez la propriété **condition** ou **UntilCondition** .

4. Cliquez sur la propriété **ConditionName** .

5. **Pour ouvrir** la boîte de dialogue **Sélectionner une condition** , cliquez **sur le curseur de sélection.**

6. Cliquez sur **nouvelle condition** pour ouvrir la boîte de dialogue **éditeur de conditions de règle** .

7. Tapez l’expression de la condition dans la zone de texte **condition** .

     Pour plus d’informations sur la création d’expressions de condition, consultez [éditeur de conditions de règle, boîte de dialogue (héritée)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8. Lorsque vous avez terminé de créer l’expression de condition, cliquez sur **OK** pour fermer la boîte de dialogue et créer la condition de règle avec un nom attribué.

     La boîte de dialogue **Sélectionner une condition** s’ouvre.

     Pour plus d’informations sur l’utilisation de la boîte de dialogue **Sélectionner une condition** , consultez boîte [de dialogue Sélectionner une condition (hérité)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Voir aussi
 [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md) [utilisant ConditionedActivityGroup](https://msdn2.microsoft.com/library/bb675237.aspx) [à l’aide de l’activité IfElseBranchActivity](https://msdn2.microsoft.com/library/bb628465.aspx) à l’aide de l' [activité duplicateur](https://msdn2.microsoft.com/library/bb628544.aspx) [à l’aide de la boîte de](https://msdn2.microsoft.com/library/bb628552.aspx) [dialogue Éditeur de conditions de règle](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) d’activité en cours (hérité) boîte de dialogue [Sélectionner une condition (hérité)](../workflow-designer/select-condition-dialog-box-legacy.md) [utilisation des conditions dans les workflows](https://msdn2.microsoft.com/library/bb628447.aspx)
