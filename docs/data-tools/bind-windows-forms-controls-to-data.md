---
title: "Comment&#160;: lier des contr&#244;les Windows Forms &#224; des donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (Windows Forms), afficher"
  - "sources de données, afficher"
  - "afficher les données, contrôles Windows Forms"
  - "Windows Forms, afficher les données"
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 28
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: lier des contr&#244;les Windows Forms &#224; des donn&#233;es
Liez des données aux contrôles Windows Forms en faisant glisser des objets de la [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md).  Avant de faire glisser des éléments de la fenêtre **Sources de données**, vous pouvez affecter au type de contrôle de la table la valeur **Détails** pour les contrôles individuels, ou **DataGridView** pour un <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
 Si les contrôles requis par votre application ne sont pas disponibles de la fenêtre **Sources de données** , vous pouvez ajouter des contrôles.  Pour plus d'informations, consultez [Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Affichage de l'intégralité d'une table de données dans des contrôles individuels  
 Vous pouvez afficher l'intégralité d'une table de données dans des contrôles individuels en faisant glisser la table \(ou un nœud représentant une collection si vous utilisez une source de données objet\) à partir de la fenêtre **Sources de données** jusqu'à un formulaire dans une application Windows.  
  
#### Pour afficher l'intégralité d'une table de données  
  
1.  Ouvrez la fenêtre **Sources de données**.  Pour plus d'informations, consultez [Comment : ouvrir la fenêtre Sources de données](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Si la fenêtre **Sources de données** est vide, ajoutez\-y une source de données.  Pour plus d'informations, consultez [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md).  
  
2.  Ouvrez le formulaire dans le **Concepteur Windows Forms**.  
  
3.  Sélectionnez une table dans la fenêtre **Sources de données**, cliquez sur la flèche de déroulement, puis sélectionnez **Détails**.  
  
4.  Faites glisser la table depuis la fenêtre **Sources de données** jusqu'à un formulaire.  
  
     Un contrôle lié aux données individuel est créé pour chaque colonne ou propriété dans le formulaire, accompagné d'un contrôle Label contenant l’intitulé.  
  
## Affichage des colonnes de données sélectionnées dans des contrôles individuels  
 Affichez des colonnes de données individuelles dans des contrôles individuels en faisant glisser des colonnes \(ou des propriétés si vous utilisez une source de données objet\) individuelles depuis la fenêtre **Sources de données** jusqu'à un formulaire dans une application Windows.  
  
#### Pour afficher des colonnes de données sélectionnées  
  
1.  Ouvrez la fenêtre **Sources de données**.  Pour plus d'informations, consultez [Comment : ouvrir la fenêtre Sources de données](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Si la fenêtre **Sources de données** est vide, ajoutez\-y une source de données.  Pour plus d'informations, consultez [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md).  
  
2.  Développez la table pour afficher les colonnes individuelles.  
  
    > [!TIP]
    >  Pour définir le contrôle qui est créé pour chaque colonne, sélectionnez la colonne dans la fenêtre **Sources de données**, cliquez sur la flèche de déroulement et sélectionnez un contrôle dans la liste des contrôles disponibles.  Pour plus d'informations, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Ouvrez le formulaire dans le **Concepteur Windows Forms**.  
  
4.  Faites glisser les colonnes désirées depuis la fenêtre **Sources de données** jusqu'à un formulaire.  
  
     Pour chaque colonne ou propriété que vous faites glisser, un contrôle lié aux données individuel est créé dans le formulaire, accompagné d'un contrôle Label contenant l’intitulé.  
  
 Vous pouvez également faire glisser des éléments de la fenêtre **Sources de données** sur des contrôles existants \(contrôles qui se trouvent déjà sur un formulaire\) pour lier le contrôle aux données.  Les liaisons de données d'un contrôle déjà lié aux données sont réinitialisées au dernier élément déplacé sur celui\-ci.  
  
> [!NOTE]
>  Pour être des cibles de déplacement valides, les contrôles doivent être capables d'afficher le type de données sous\-jacent de l'élément déplacé depuis la fenêtre **Sources de données**.  Par exemple, le déplacement d'un élément possédant un type de données <xref:System.DateTime> jusqu'à <xref:System.Windows.Forms.CheckBox> n'est pas valide, car <xref:System.Windows.Forms.CheckBox> n'est pas capable d'afficher une date.  
  
#### Pour lier un contrôle existant à des données  
  
1.  Ouvrez la fenêtre **Sources de données**.  Pour plus d'informations, consultez [Comment : ouvrir la fenêtre Sources de données](../data-tools/how-to-open-the-data-sources-window.md).  
  
2.  Ouvrez le formulaire dans [Windows Forms Designer](http://msdn.microsoft.com/fr-fr/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
3.  Développez une table ou un objet dans la fenêtre **Sources de données** pour afficher ses colonnes ou propriétés individuelles.  
  
4.  Faites glisser l'élément désiré depuis la fenêtre **Sources de données** jusqu'à un contrôle existant.  
  
     Le contrôle est maintenant lié à cet élément sélectionné.  
  
## Affichage des données dans un contrôle DataGridView  
  
#### Pour afficher des données dans un nouveau contrôle DataGridView de Windows Forms  
  
1.  Ouvrez la fenêtre **Sources de données**.  Pour plus d'informations, consultez [Comment : ouvrir la fenêtre Sources de données](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Si la fenêtre **Sources de données** est vide, ajoutez\-y une source de données.  Pour plus d'informations, consultez [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md).  
  
2.  Ouvrez le formulaire dans le **Concepteur Windows Forms**.  
  
3.  Sélectionnez une table dans la fenêtre **Sources de données**, cliquez sur la flèche de déroulement, puis sélectionnez **DataGridView**.  
  
4.  Faites glisser la table depuis la fenêtre **Sources de données** jusqu'à un formulaire.  
  
     Un contrôle <xref:System.Windows.Forms.DataGridView> et une barre d'outils \(<xref:System.Windows.Forms.BindingNavigator>\) de navigation au sein des enregistrements apparaissent sur le formulaire.  Un [DataSet](../data-tools/dataset-tools-in-visual-studio.md), un [TableAdapter](../data-tools/tableadapter-overview.md), un <xref:System.Windows.Forms.BindingSource> et un <xref:System.Windows.Forms.BindingNavigator> apparaissent dans la barre d'état des composants.  
  
#### Pour afficher les données dans un contrôle DataGridView existant de Windows Forms  
  
1.  Ouvrez la fenêtre **Sources de données**.  Pour plus d'informations, consultez [Comment : ouvrir la fenêtre Sources de données](../data-tools/how-to-open-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Si la fenêtre **Sources de données** est vide, ajoutez\-y une source de données.  Pour plus d'informations, consultez [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md).  
  
2.  Ouvrez votre formulaire dans le **Concepteur Windows Forms**.  
  
3.  Sélectionnez une table dans la fenêtre **Sources de données**, cliquez sur la flèche de déroulement, puis sélectionnez **DataGridView**.  
  
4.  Faites glisser la table depuis la fenêtre **Sources de données** jusqu'à un <xref:System.Windows.Forms.DataGridView> situé sur le formulaire.  
  
     Le contrôle <xref:System.Windows.Forms.DataGridView> est maintenant lié à la table que vous avez déplacée sur celui\-ci.  Un [DataSet](../data-tools/dataset-tools-in-visual-studio.md), un [TableAdapter](../data-tools/tableadapter-overview.md) et un <xref:System.Windows.Forms.BindingSource> apparaissent dans la barre d'état des composants.  
  
## Voir aussi  
 [Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Vue d'ensemble du composant BindingSource](../Topic/BindingSource%20Component%20Overview.md)   
 [Vue d'ensemble du contrôle BindingNavigator](../Topic/BindingNavigator%20Control%20Overview%20\(Windows%20Forms\).md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)   
 [Outils permettant d'utiliser des sources de données dans Visual Studio](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)