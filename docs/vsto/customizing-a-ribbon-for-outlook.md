---
title: "Personnalisation d&#39;un ruban pour Outlook"
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
  - "ruban personnalisé, à propos de la personnalisation du ruban"
  - "personnaliser le ruban, à propos de la personnalisation du ruban"
  - "inspecteurs (développement Office dans Visual Studio)"
  - "Outlook (développement Office dans Visual Studio), ruban"
  - "ruban (développement Office dans Visual Studio), Outlook"
ms.assetid: 11d10e72-806d-4d5e-b080-139bd8633eaa
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Personnalisation d&#39;un ruban pour Outlook
  Quand vous personnalisez le ruban dans Microsoft Office Outlook, vous devez prendre en compte l'emplacement où votre ruban personnalisé apparaîtra dans l'application.  Outlook affiche le ruban dans l'interface utilisateur principale de l'application et dans les fenêtres qui s'ouvrent lorsque les utilisateurs effectuent certaines tâches, telles que la création de messages électroniques.  Ces fenêtres d'application sont appelées inspecteurs.  
  
 ![lien vers la vidéo](../vsto/media/playvideo.png "lien vers la vidéo") Pour visionner la démonstration vidéo associée, consultez [Comment : utiliser Concepteur de ruban pour personnaliser le ruban dans Outlook](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Ajout d'un ruban personnalisé à l'interface utilisateur de l'application principale  
 L'interface utilisateur de l'application principale dans Outlook est appelée l'Explorateur.  Si vous utilisez l'élément **Ruban \(Concepteur visuel\)**, vous pouvez ajouter un ruban à l'Explorateur en cliquant sur la propriété **RibbonType** du ruban dans la fenêtre **Propriétés**, puis en sélectionnant **Microsoft.Outlook.Explorer**.  
  
## Affectation d'un ruban à un inspecteur  
 Pour identifier l'inspecteur que vous souhaitez personnaliser, vous spécifiez le type de ruban qui correspond à la classe de message de l'inspecteur.  
  
 Si vous utilisez l'élément **Ruban \(Concepteur visuel\)**, cliquez sur la propriété **RibbonType** du ruban dans la fenêtre **Propriétés**, puis sélectionnez un ou plusieurs ID de ruban dans la liste des valeurs.  
  
 Vous pouvez ajouter plusieurs rubans à un projet.  Si plusieurs rubans partagent un ID de ruban, substituez la méthode CreateRibbonExtensibilityObject de la classe `ThisAddin` de votre projet pour spécifier le ruban à afficher au moment de l'exécution.  Pour plus d'informations, consultez [Vue d'ensemble du ruban](../vsto/ribbon-overview.md).  Pour plus d'informations sur chaque type de ruban, consultez l'article technique [Personnalisation du ruban dans Outlook 2007](http://msdn.microsoft.com/fr-fr/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## Spécification du type de ruban à l'aide du code XML du ruban  
 Si vous utilisez l'élément **Ruban \(XML\)**, vérifiez la valeur du paramètre *ribbonID* de la méthode <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> et retournez le ruban approprié.  
  
 La méthode <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> est automatiquement générée par Visual Studio dans le fichier de code du ruban.  Le paramètre *ribbonID* est une chaîne qui identifie l'Explorateur ou un type spécifique d'inspecteur.  Pour obtenir la liste complète des valeurs possibles du paramètre *ribbonID*, consultez l'article technique [Personnalisation du ruban dans Outlook 2007](http://msdn.microsoft.com/fr-fr/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 L'exemple de code suivant montre comment afficher un ruban personnalisé uniquement dans l' inspecteur `Microsoft.Outlook.Mail.Compose`.  Il s'agit de l'inspecteur qui s'affiche lorsqu'un utilisateur crée un message électronique.  Le ruban à afficher est spécifié dans la méthode `GetResourceText()`, générée dans la classe **Ribbon**.  Pour plus d'informations sur la classe **Ribbon**, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/CS/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/VB/Ribbon1.vb#1)]  
  
## Voir aussi  
 [Accès au ruban au moment de l'exécution](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)  
  
  