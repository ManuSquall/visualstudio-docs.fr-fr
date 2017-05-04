---
title: "Comment&#160;: remplir des documents avec les donn&#233;es d&#39;objets | Microsoft Docs"
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
  - "documents (développement Office dans Visual Studio), remplissage à l’aide de données"
  - "données (développement Office dans Visual Studio), ajout à des documents"
ms.assetid: 83e6ebac-e468-4bef-a91c-78c7bf597a75
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Comment&#160;: remplir des documents avec les donn&#233;es d&#39;objets
  Vous pouvez accéder aux projets au niveau du document pour Microsoft Office en procédant de la même façon que pour les projets Windows Forms. Vous utilisez les mêmes outils et le même code pour importer les données d’un objet dans votre solution. Par ailleurs, vous pouvez utiliser des contrôles Windows Forms pour afficher les données. En outre, vous pouvez afficher les données à l'aide de contrôles hôtes. Les contrôles hôtes sont des objets natifs dans Microsoft Office Word qui ont été améliorés avec les événements et la fonctionnalité de liaison de données. Pour plus d'informations, consultez [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Vous devez effectuer trois étapes de base pour remplir le document à l’aide des données d’un objet :  
  
-   Ajoutez un contrôle au document que vous pouvez lier aux données.  
  
-   Ajoutez un objet de données au document.  
  
-   Connectez l’objet de données à BindingSource.  
  
## Ajout d’un objet de données  
  
#### Pour ajouter un objet de données  
  
-   Ouvrez la fenêtre **Sources de données**, puis créez une source de données à partir d’un objet. Pour plus d'informations, consultez [Comment : se connecter à des données dans des objets](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
## Connexion de l’objet de données à BindingSource  
 Dans les projets au niveau du document, vous ajoutez les contrôles à votre document et les liez aux données au moment du design.  
  
 Dans les projets de complément VSTO, vous créez les contrôles et les liez au moment de l’exécution.  
  
### Projets au niveau du document  
  
##### Pour connecter l’objet de données à BindingSource  
  
1.  Faites glisser le champ de données que vous souhaitez de la fenêtre **Sources de données** vers votre document. Cela entraîne la création automatique d’un contrôle.  
  
2.  Dans votre code, créez une instance du type de l’objet que vous avez choisi pour la source de données.  
  
3.  Assignez l’instance à la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> de <xref:System.Windows.Forms.BindingSource>.  
  
### Projets de niveau application  
  
##### Pour connecter l’objet de données à BindingSource  
  
1.  Dans votre code, créez une instance du type de l’objet associé à la source de données.  
  
2.  Créez une instance de <xref:System.Windows.Forms.BindingSource>.  
  
3.  Assignez l’instance de la source de données à la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> de <xref:System.Windows.Forms.BindingSource>.  
  
4.  Ajoutez la source de données en tant que liaison de données au contrôle.  
  
## Voir aussi  
 [Liaison de données aux contrôles dans les solutions Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Comment : remplir des documents avec les données d'une base de données](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Comment : mettre à jour une source de données avec les données d'un contrôle hôte](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Connexion à des données dans des applications Windows Forms](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Vue d'ensemble du composant BindingSource](../Topic/BindingSource%20Component%20Overview.md)  
  
  