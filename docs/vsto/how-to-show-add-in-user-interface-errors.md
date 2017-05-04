---
title: "Comment&#160;: afficher les erreurs de l&#39;interface utilisateur du compl&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "compléments (développement Office dans Visual Studio), erreurs d’interface utilisateur"
  - "erreurs (développement Office dans Visual Studio), erreurs d’interface utilisateur"
  - "interfaces utilisateur (développement Office dans Visual Studio), erreurs"
  - "compléments de niveau application (développement Office dans Visual Studio), erreurs d’interface utilisateur"
ms.assetid: aa82cc04-e616-4501-940c-79d11fb393cc
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Comment&#160;: afficher les erreurs de l&#39;interface utilisateur du compl&#233;ment
  Par défaut, si un complément VSTO tente de manipuler l’interface utilisateur de Microsoft Office et qu’il échoue, aucun message d’erreur n’est affiché. Toutefois, vous pouvez configurer les applications Microsoft Office pour afficher des messages en cas d’erreur liée à l’interface utilisateur. Vous pouvez utiliser ces messages pour vous aider à déterminer pourquoi un ruban personnalisé n’est pas affiché, ou pourquoi un ruban apparaît mais pas les contrôles.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Pour afficher les erreurs d’interface utilisateur du complément VSTO  
  
1.  Démarrez l’application.  
  
2.  Cliquez sur l'onglet **Fichier**.  
  
3.  Cliquez sur **Options**.  
  
4.  Dans le volet des catégories, cliquez sur **Avancé**.  
  
5.  Dans le volet d’informations, sélectionnez **Afficher les erreurs d’interface utilisateur du complément VSTO**, puis cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Pour Outlook, la case à cocher **Afficher les erreurs d’interface utilisateur du complément VSTO** se trouve dans la section **Développeur** du volet d’informations. Pour les autres applications, elle se trouve dans la section **Général** du volet d’informations.  
  
## Voir aussi  
 [Personnalisation de l'interface utilisateur Office](../vsto/office-ui-customization.md)   
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Vue d'ensemble du volet Actions](../vsto/actions-pane-overview.md)  
  
  