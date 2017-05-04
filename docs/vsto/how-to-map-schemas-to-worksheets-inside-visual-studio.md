---
title: "Comment&#160;: mapper des sch&#233;mas &#224; des feuilles de calcul dans Visual Studio | Microsoft Docs"
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
  - "Excel (développement Office dans Visual Studio), schémas XML"
  - "mappages (développement Office dans Visual Studio), schémas XML aux feuilles de calcul Excel"
  - "feuilles de calcul (développement Office dans Visual Studio), schémas XML"
  - "schémas XML (développement Office dans Visual Studio), mapper"
ms.assetid: cef3f751-c1cf-46f3-9177-0bacdcee4121
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Comment&#160;: mapper des sch&#233;mas &#224; des feuilles de calcul dans Visual Studio
  Vous pouvez mapper un schéma XML à une feuille de calcul ouverte dans Visual Studio.  Vous utilisez les mêmes outils Microsoft Office Excel que lorsque le classeur est ouvert en dehors de Visual Studio.  Le projet Office crée les mêmes objets que vous mappiez le schéma à la feuille de calcul avant ou après avoir créé votre solution Excel.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Vous ne pouvez pas utiliser des schémas XML multipart dans les solutions Excel.  
  
### Pour mapper un schéma XML à une feuille de calcul Excel dans Visual Studio  
  
1.  Ouvrez le classeur Excel ou le projet de modèle dans Visual Studio.  
  
2.  Cliquez dans la feuille de calcul pour déplacer le focus sur le concepteur.  
  
3.  Dans le ruban, cliquez sur l'onglet **Développeur**.  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez préalablement l'afficher.  Pour plus d’informations, consultez [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Dans le groupe **XML**, cliquez sur **Source**.  
  
     La fenêtre **Source XML** s'affiche.  
  
5.  Dans la fenêtre **Source XML**, cliquez sur **Mappages XML**.  
  
     La boîte de dialogue **Mappages XML** s'ouvre.  
  
6.  Dans la boîte de dialogue **Mappages XML**, cliquez sur **Ajouter**.  
  
7.  Recherchez votre fichier schéma, sélectionnez\-le, puis cliquez sur **Ouvrir**.  
  
8.  Cliquez sur **OK**.  
  
     Le schéma est représenté dans la fenêtre **Source XML**.  Dans votre projet, un <xref:System.Data.DataSet> typé est généré à partir du schéma, et une <xref:System.Windows.Forms.BindingSource> est créée.  
  
9. Faites glisser les éléments de la fenêtre **Source XML** aux endroits de votre feuille de calcul où vous souhaitez que les contrôles correspondants soient créés.  
  
     Si vous faites glisser un élément de schéma non répétitif, le projet Office crée un contrôle d' <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> qui est automatiquement lié à <xref:System.Windows.Forms.BindingSource>.  
  
     Si vous faites glisser un élément de schéma répétitif, le projet Office crée un contrôle d' <xref:Microsoft.Office.Tools.Excel.ListObject> qui n'est pas lié automatiquement à une source de données.  Pour plus d’informations, consultez [Schémas et données XML dans les personnalisations au niveau du document](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## Voir aussi  
 [Comment : mapper des schémas à des documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Schémas et données XML dans les personnalisations au niveau du document](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  