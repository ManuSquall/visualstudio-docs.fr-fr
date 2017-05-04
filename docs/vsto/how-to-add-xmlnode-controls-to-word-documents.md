---
title: "Comment&#160;: ajouter des contr&#244;les XMLNode &#224; des documents Word | Microsoft Docs"
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
  - "contrôles (développement Office dans Visual Studio), ajouter à des documents"
  - "XMLNode (contrôle), ajouter à des documents"
ms.assetid: d583b9d4-bd13-46e3-9eb7-da18fcb7eb8c
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Comment&#160;: ajouter des contr&#244;les XMLNode &#224; des documents Word
  **important** les informations présentées dans cette rubrique concernant Microsoft Word est présenté exclusivement pour l'avantage et l'utilisation des personnes et organisations qui se trouvent en dehors de les états\-unis et de ses territoires ou qui utilisent, ou de développer des programmes qui s'exécutent sur, les produits Microsoft Word qui ont été autorisés par Microsoft avant janvier 2010, lorsque Microsoft a supprimé une implémentation de fonctionnalités spécifique liée à une personnalisée XML Microsoft Word.  Ces informations liées à Microsoft Word ne peuvent pas être lues ou utilisées par des individus ou des organisations se trouvant aux États\-Unis ou dans ses territoires qui utilisent, ou développent des programmes exécutés avec, des produits Microsoft Word dont la licence Microsoft est postérieure à janvier 2010 ; ces produits n'auront pas le même comportement que ceux dont la licence est antérieure à cette date ou ceux qui ont été achetés ou ont bénéficié d'une licence d'utilisation en dehors des États\-Unis.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Lorsque vous mappez un élément de schéma XML non\-répétitif à un document Microsoft Office Word, Visual Studio ajoute automatiquement un contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> à votre document.  Pour plus d'informations sur le mappage d'éléments de schéma XML répétitifs, consultez [Comment : ajouter des contrôles XMLNodes à des documents Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md).  
  
> [!NOTE]  
>  Le contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> n'est pas disponible dans la **Boîte à outils** ou la fenêtre **Sources de données**, et il ne peut pas être créé par programme.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Pour ajouter un contrôle XMLNode à un document  
  
1.  Dans le document ouvert dans le concepteur Visual Studio, sur le ruban, cliquez sur l'onglet **Développeur**.  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez préalablement l'afficher.  Pour plus d’informations, consultez [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  Dans le groupe **XML**, cliquez sur **Schéma**.  
  
     La boîte de dialogue **Modèles et compléments** s'ouvre.  
  
3.  Cliquez sur l'onglet **Schéma XML**.  
  
4.  Cliquez sur **Ajouter un schéma**.  
  
     La boîte de dialogue **Ajouter un schéma** s'affiche.  
  
5.  Dans la boîte de dialogue **Ajouter un schéma**, sélectionnez un schéma XML contenant des éléments de schéma non répétitifs et cliquez sur **Ouvrir**.  
  
     La boîte de dialogue **Paramètres du schéma** s'affiche.  
  
6.  Assignez un alias ou cliquez sur **OK** pour ajouter le schéma sans alias.  
  
     Le schéma est ajouté à la boîte de dialogue **Ajouter un schéma**.  
  
7.  Dans la boîte de dialogue **Ajouter un schéma**, cliquez sur **OK**.  
  
8.  Le volet de tâches **Structure XML** s'affiche.  
  
9. Cliquez sur l'élément de schéma non répétitif dans le volet de tâches **Structure XML** pour l'ajouter au document.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Word.XMLNode> est alors créé et ajouté au projet.  
  
## Voir aussi  
 [XMLNode, contrôle](../vsto/xmlnode-control.md)   
 [Automatisation de Word à l'aide d'objets étendus](../vsto/automating-word-by-using-extended-objects.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  