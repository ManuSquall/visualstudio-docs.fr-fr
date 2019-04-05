---
title: 'Procédure : Créer un ensemble de règles PolicyActivity (hérité) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5e7528e8a589cb64e4debc8c1e119f8f59a6244c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948674"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Procédure : Créer un ensemble de règles PolicyActivity (hérité)
Cette rubrique décrit comment créer un ensemble de règles d'activité de stratégie à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Après avoir fait glisser un **stratégie** élément d’activité à partir de la **boîte à outils** vers l’aire de conception de flux de travail, vous pouvez sélectionner une règle existante ou créer un ensemble de règles pour le [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) activité. Vous sélectionnez une règle existante, définie à l’aide de la [sélectionnez règle boîte de dialogue (hérité)](../workflow-designer/select-rule-set-dialog-box-legacy.md) et que vous créez des ensembles de règles à l’aide de la [règle éditeur de boîte de dialogue (hérité)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  Vous pouvez ouvrir le [règle éditeur de boîte de dialogue (hérité)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) boîte de dialogue directement en double-cliquant sur un [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) activité qui se trouve sur l’aire de conception de flux de travail.  
  
### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Pour sélectionner ou créer un ensemble de règles pour une activité PolicyActivity  
  
1.  Avec le bouton droit le [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), puis cliquez sur **propriétés** pour ouvrir le **propriétés** fenêtre.  
  
2.  Cliquez sur le **RuleSetReference** propriété.  
  
3.  Effectuez l’une des opérations suivantes :  
  
    -   Cliquez sur le **RuleSetReference** ellipses **[...]** , puis sélectionnez une règle existante, définie le [sélectionnez règle boîte de dialogue (hérité)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Passez à l'étape 10.  
  
         - ou -  
  
    -   Tapez un nom d'ensemble de règles. Cliquez sur le **RuleSetReference** ellipses **[...]** , puis sélectionnez **modifier** dans le [sélectionnez règle boîte de dialogue (hérité)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         - ou -  
  
    -   Tapez un nom d'ensemble de règles. Développez le **RuleSetReference** et sélectionnez les points de suspension **[...]**  dans le **RuleSet Definition** propriété.  
  
         Le [règle éditeur de boîte de dialogue (hérité)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) s’ouvre.  
  
4.  Dans le [règle éditeur de boîte de dialogue (hérité)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), cliquez sur **ajouter une règle** pour ajouter une nouvelle règle à l’ensemble de règles.  
  
5.  Entrez le **nom**, **priorité**, et **réévaluation** propriétés, ou conservez les valeurs par défaut.  
  
6.  Entrez le texte pour le **Condition**.  
  
7.  Entrez le texte pour le **Actions Then** et **Actions Else**.  
  
8.  Cliquez sur **ajouter une règle** à nouveau pour ajouter une autre règle.  
  
9. Quand vous avez terminé, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Sélectionnez la règle ensemble, boîte de dialogue (hérité)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Ensemble de règles éditeur boîte de dialogue (hérité)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [À l’aide de l’activité de stratégie](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)