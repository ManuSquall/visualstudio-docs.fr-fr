---
title: "Comment&#160;: personnaliser un onglet int&#233;gr&#233; | Microsoft Docs"
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
  - "onglets intégrés (développement Office dans Visual Studio)"
  - "ruban (développement Office dans Visual Studio), onglets"
ms.assetid: 197a7aaa-a51d-496c-b904-b9421849fad9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Comment&#160;: personnaliser un onglet int&#233;gr&#233;
  Vous pouvez ajouter des groupes et des contrôles à un onglet intégré.  Un onglet intégré est un onglet qui existe déjà sur le ruban d'une application Microsoft Office.  Par exemple, l'onglet **Données** est un onglet intégré dans Excel.  Lorsque vous créez un groupe personnalisé, il apparaît en dernier sous l'onglet, mais vous pouvez déplacer votre groupe n'importe où sur l'onglet.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Vous pouvez ajouter des groupes à un onglet intégré, mais vous ne pouvez pas supprimer les groupes intégrés d'un onglet intégré.  
  
### Pour ajouter des groupes à un onglet intégré  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier de code du ruban, puis cliquez sur **Concepteur de vues**.  
  
    > [!NOTE]  
    >  Si le fichier de code du ruban n'apparaît pas dans **l'Explorateur de solutions**, vous devez ajouter un **élément ruban** à votre projet.  Consultez [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Cliquez avec le bouton droit sur un onglet du Concepteur de ruban, puis cliquez sur**Propriétés**.  
  
3.  Dans la fenêtre **Propriétés**, développez la propriété **ControlId**, puis affectez à la propriété **ControlIdType** la valeur **Office**.  
  
4.  Définissez la propriété **OfficeId** avec la valeur de l'*ID de contrôle* de l'onglet intégré que vous souhaitez personnaliser.  
  
     L'ID de contrôle est le nom qui identifie de façon unique les onglets, les groupes et les contrôles qui sont intégrés aux applications Microsoft Office.  
  
     Pour obtenir la liste des ID de contrôle, consultez [Fichiers d'aide Office 2010 : identificateurs de contrôle d'Interface utilisateur Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
5.  Dans l'onglet **Contrôles de ruban Office** de la **Boîte à outils**, faites glisser un bouton sur l'onglet.  
  
    > [!NOTE]  
    >  Les groupes intégrés n'apparaissent pas dans le concepteur.  Par conséquent, la seule façon de déterminer si vous utilisez un onglet intégré consiste à examiner la propriété **ControlId** de l'onglet.  
  
### Pour positionner des groupes sur un onglet intégré  
  
1.  Dans le Concepteur de ruban, sélectionnez un groupe personnalisé.  
  
2.  Dans la fenêtre **Propriétés**, développez la propriété **Position**.  
  
3.  Affectez à la propriété **PositionType** la valeur appropriée :  
  
    -   **BeforeOfficeId** place le groupe avant un groupe intégré spécifié.  
  
    -   **AfterOfficeId** place le groupe après un groupe intégré spécifié.  
  
4.  Définissez la propriété **OfficeId** avec l'ID de contrôle d'un groupe intégré.  
  
     Pour obtenir la liste des ID de contrôle, consultez [Fichiers d'aide Office 2010 : identificateurs de contrôle d'Interface utilisateur Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## Voir aussi  
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide d'un élément XML Ribbon](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Comment : modifier la position d'un onglet dans le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Comment : afficher les erreurs de l'interface utilisateur du complément](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  