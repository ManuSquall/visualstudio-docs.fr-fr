---
title: 'Comment : créer un ensemble de règles PolicyActivity (héritée) | Documents Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4911912aa46f5dc8a6aea9b9b20e87c1f83e576f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Procédure : créer un ensemble de règles PolicyActivity (héritée)

Cette rubrique décrit comment créer une règle d’activité de stratégie définie à l’aide de Windows Workflow Designer hérité qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Une fois que vous avez fait glisser un **stratégie** élément d’activité à partir de la **boîte à outils** vers l’aire de conception du flux de travail, vous devez sélectionner une règle existante ou créer une règle définie pour le [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) activité. Vous sélectionnez une règle existante, définie à l’aide de la [sélectionnez règle définie boîte de dialogue (héritée)](../workflow-designer/select-rule-set-dialog-box-legacy.md) et créer des ensembles de règles à l’aide de la [boîte règle définie éditeur de boîte de dialogue (héritée)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> Vous pouvez ouvrir le [boîte règle définie éditeur de boîte de dialogue (héritée)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) boîte de dialogue directement en double-cliquant sur un [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) activité qui se trouve sur l’aire de conception de flux de travail.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Pour sélectionner ou créer un ensemble de règles pour une activité PolicyActivity

1.  Avec le bouton droit le [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), puis cliquez sur **propriétés** pour ouvrir le **propriétés** fenêtre.

2.  Cliquez sur le **RuleSetReference** propriété.

3.  Effectuez l’une des opérations suivantes :

    -   Cliquez sur le **RuleSetReference** points de suspension **[...]** , puis sélectionnez une règle existante, définie dans le [sélectionnez règle définie boîte de dialogue (héritée)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Passez à l'étape 10.

         ou

    -   Tapez un nom d'ensemble de règles. Cliquez sur le **RuleSetReference** points de suspension **[...]** , puis sélectionnez **modifier** dans les [sélectionnez règle définie boîte de dialogue (héritée)](../workflow-designer/select-rule-set-dialog-box-legacy.md).

         - ou -

    -   Tapez un nom d'ensemble de règles. Développez le **RuleSetReference** et sélectionnez les points de suspension **[...]**  dans les **RuleSet Definition** propriété.

         Le [boîte règle définie éditeur de boîte de dialogue (héritée)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) s’ouvre.

4.  Dans le [boîte règle définie éditeur de boîte de dialogue (héritée)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), cliquez sur **ajouter une règle** pour ajouter une nouvelle règle à l’ensemble de règles.

5.  Entrez le **nom**, **priorité**, et **réévaluation** propriétés, ou conserver les valeurs par défaut.

6.  Entrez le texte pour le **Condition**.

7.  Entrez le texte pour le **Actions Then** et **Actions Else**.

8.  Cliquez sur **ajouter une règle** à nouveau pour ajouter une autre règle.

9. Quand vous avez terminé, cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

- [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)
- [Sélectionner l’ensemble de règles, boîte de dialogue (hérité)](../workflow-designer/select-rule-set-dialog-box-legacy.md)
- [Éditeur d’ensemble de règles, boîte de dialogue (hérité)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)
- [À l’aide de l’activité de stratégie](http://go.microsoft.com/fwlink?LinkID=65004)
- [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)