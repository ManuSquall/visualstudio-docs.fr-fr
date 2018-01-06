---
title: "Comment : créer un ensemble de règles PolicyActivity (héritée) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 1b57fe5f33bdbc4dfb7ab76856bdd80a3246ea9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Procédure : créer un ensemble de règles PolicyActivity (héritée)
Cette rubrique décrit comment créer un ensemble de règles d'activité de stratégie à l'aide du [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Une fois que vous avez fait glisser un **stratégie** élément d’activité à partir de la **boîte à outils** vers l’aire de conception du flux de travail, vous devez sélectionner une règle existante ou créer une règle définie pour le [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) activité. Vous sélectionnez une règle existante, définie à l’aide de la [sélectionnez règle définie boîte de dialogue (héritée)](../workflow-designer/select-rule-set-dialog-box-legacy.md) et créer des ensembles de règles à l’aide de la [boîte règle définie éditeur de boîte de dialogue (héritée)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  Vous pouvez ouvrir le [boîte règle définie éditeur de boîte de dialogue (héritée)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) boîte de dialogue directement en double-cliquant sur un [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) activité qui se trouve sur l’aire de conception de flux de travail.  
  
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
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Boîte de dialogue Sélectionnez la règle définir (hérité)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Ensemble de règles éditeur boîte de dialogue (héritée)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [À l’aide de l’activité de stratégie](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)