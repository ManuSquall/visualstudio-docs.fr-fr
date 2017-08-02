---
title: "Comment&#160;: modifier la position d&#39;un onglet dans le ruban"
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
  - "ruban (développement Office dans Visual Studio), onglets"
ms.assetid: 3f0906e3-9708-4136-ac49-986bc4c92ea4
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Comment&#160;: modifier la position d&#39;un onglet dans le ruban
  Vous pouvez modifier l'ordre des onglets personnalisés sur un Ruban à l'aide de l'**Éditeur de collections d'onglets**.  Vous pouvez positionner les onglets personnalisés avant ou après un onglet prédéfini du ruban.  Un onglet intégré est un onglet qui figure déjà sur le ruban d'une application Microsoft Office.  Par exemple, l'onglet **Données** est un onglet intégré dans Excel.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Pour modifier l'ordre des onglets sur le ruban  
  
1.  Sélectionnez le fichier de code du ruban \(fichier .vb ou .cs\) dans l'**Explorateur de solutions**.  
  
2.  Dans le menu **Affichage**, cliquez sur **Concepteur**.  
  
3.  Cliquez avec le bouton droit sur le Concepteur de ruban, puis cliquez sur **Propriétés**.  
  
4.  Dans la fenêtre **Propriétés**, sélectionnez la propriété **Tabs**, puis cliquez sur le bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](~/docs/sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")\).  
  
     L'**Éditeur de collections Tab** s'affiche.  
  
5.  Dans la liste **Membres** de l'**Éditeur de collections Tab**, sélectionnez l'onglet à déplacer et cliquez sur la flèche Haut ou Bas pour modifier l'ordre des onglets.  
  
### Pour positionner un onglet avant ou après un onglet intégré du ruban  
  
1.  Dans le Concepteur de ruban, sélectionnez un onglet personnalisé.  
  
2.  Dans la fenêtre **Propriétés** , développez la propriété **ControlId** , puis vérifiez que la valeur de la propriété **ControlIdType** a la valeur **Personnalisé**.  
  
3.  Dans la fenêtre **Propriétés**, développez la propriété **Position**.  
  
4.  Affectez la valeur appropriée à la propriété **PositionType**.  
  
    -   **BeforeOfficeId** positionne l'onglet avant l'onglet prédéfini spécifié.  
  
    -   **AfterOfficeId** positionne l'onglet après l'onglet prédéfini spécifié.  
  
5.  Affectez à la propriété **OfficeId** l'ID du contrôle d'un onglet prédéfini.  
  
     Pour obtenir la liste des ID de contrôle, consultez [Office 2010 fichiers d'aide suivantes : Identificateurs de contrôle d'interface utilisateur Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## Voir aussi  
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide d'un élément XML Ribbon](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  