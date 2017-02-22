---
title: "Proc&#233;dure&#160;: cr&#233;er un ensemble de r&#232;gles PolicyActivity (h&#233;rit&#233;e) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "PolicyActivity (activité), création d'ensembles de règles"
  - "PolicyActivity (activité), sélectionner des ensembles de règles"
  - "Éditeur d'ensemble de règles (boîte de dialogue)"
  - "ensembles de règles, créer pour PolicyActivity"
  - "Sélectionner l'ensemble de règles (boîte de dialogue)"
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Proc&#233;dure&#160;: cr&#233;er un ensemble de r&#232;gles PolicyActivity (h&#233;rit&#233;e)
Cette rubrique décrit comment créer un ensemble de règles d'activité de stratégie à l'aide du [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Après avoir fait glisser un élément d'activité **Stratégie** de la **boîte à outils** vers l'aire de conception de workflow, vous pouvez sélectionner une règle existante ou créer un ensemble de règles pour l'activité [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019).Vous sélectionnez un ensemble de règles existant à l'aide de la [Sélectionner l'ensemble de règles, boîte de dialogue \(héritée\)](../workflow-designer/select-rule-set-dialog-box-legacy.md) et vous créez des ensembles de règles à l'aide de la [Éditeur d'ensemble de règles, boîte de dialogue \(héritée\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  Vous pouvez ouvrir directement la boîte de dialogue Éditeur d'ensemble de règles \(voir [Éditeur d'ensemble de règles, boîte de dialogue \(héritée\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)\) en double\-cliquant sur une activité [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) se trouvant dans l'aire de conception du workflow.  
  
### Pour sélectionner ou créer un ensemble de règles pour une activité PolicyActivity  
  
1.  Cliquez avec le bouton droit sur [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), puis cliquez sur **Propriétés** pour ouvrir la fenêtre **Propriétés**.  
  
2.  Cliquez sur la propriété **RuleSetReference**.  
  
3.  Effectuez l'une des opérations suivantes :  
  
    -   Cliquez sur les boutons de sélection de **RuleSetReference** \(**\[.\]**\), puis sélectionnez un ensemble de règles existant dans la [Sélectionner l'ensemble de règles, boîte de dialogue \(héritée\)](../workflow-designer/select-rule-set-dialog-box-legacy.md).Passez à l'étape 10.  
  
         \- ou \-  
  
    -   Tapez un nom d'ensemble de règles.Cliquez sur les boutons de sélection de **RuleSetReference**\( **\[.\]**\), puis sélectionnez **Modifier** dans la [Sélectionner l'ensemble de règles, boîte de dialogue \(héritée\)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         ou  
  
    -   Tapez un nom d'ensemble de règles.Développez la propriété **RuleSetReference** et sélectionnez le bouton de sélection **\[…\]** dans la propriété **RuleSet Definition**.  
  
         La [Éditeur d'ensemble de règles, boîte de dialogue \(héritée\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) s'ouvre.  
  
4.  Dans la [Éditeur d'ensemble de règles, boîte de dialogue \(héritée\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), cliquez sur **Ajouter une règle** pour ajouter une nouvelle règle à l'ensemble de règles.  
  
5.  Entrez le **Nom**, la **Priorité** et les propriétés de **Réévaluation** ou gardez les valeurs par défaut.  
  
6.  Entrez le texte de la **Condition**.  
  
7.  Entrez le texte correspondant dans **Actions THEN** et **Actions ELSE**.  
  
8.  Cliquez de nouveau sur **Ajouter une règle** pour ajouter une autre règle.  
  
9. Lorsque vous avez terminé, cliquez sur **OK**.  
  
## Voir aussi  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Sélectionner l'ensemble de règles, boîte de dialogue \(héritée\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Éditeur d'ensemble de règles, boîte de dialogue \(héritée\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Utilisation de l'activité de stratégie](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Activités de workflow héritées](../workflow-designer/legacy-workflow-activities.md)