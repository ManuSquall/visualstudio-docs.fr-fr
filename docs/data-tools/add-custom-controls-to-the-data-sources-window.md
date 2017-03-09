---
title: "Ajouter des contr&#244;les personnalis&#233;s &#224; la fen&#234;tre Sources de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.howtoaddcustomcontrol"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Sources de données (fenêtre), ajout de contrôles"
  - "contrôles (Visual Studio), ajout à la fenêtre Sources de données"
  - "DefaultBindingPropertyAttribute (classe), utilisation"
  - "LookupBindingPropertiesAttribute (classe), utilisation"
  - "ComplexBindingPropertiesAttribute (classe), utilisation"
  - "Sources de données (fenêtre), sélection des contrôles"
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 42
caps.handback.revision: 39
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ajouter des contr&#244;les personnalis&#233;s &#224; la fen&#234;tre Sources de donn&#233;es
Lorsque vous faites glisser un élément de la fenêtre **Sources de données** vers une aire de conception pour créer un contrôle lié aux données, vous pouvez sélectionner le type de contrôle que vous créez.  Chaque élément dans la fenêtre comporte une liste déroulante qui affiche les contrôles parmi lesquels effectuer votre choix.  L'ensemble de contrôles associé pour chaque élément est déterminé par le type de données de l'élément.  Si le contrôle que vous souhaitez créer ne s'affiche pas dans la liste, vous pouvez suivre les instructions de cette rubrique pour l'ajouter à la liste.  
  
 Pour plus d'informations sur la sélection de contrôles liés aux données afin de créer des éléments dans la fenêtre **Sources de données**, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="customizinglist"></a> Personnalisation de la liste des contrôles pouvant être liés pour un type de données  
 Exécutez les étapes suivantes pour ajouter ou supprimer des contrôles dans la liste des contrôles disponibles pour les éléments de la fenêtre **Sources de données** qui ont un type de données spécifique.  
  
#### Pour sélectionner les contrôles à répertorier pour un type de données  
  
1.  Assurez\-vous que le Concepteur WPF ou le Concepteur Windows Forms est ouvert.  
  
2.  Dans la fenêtre **Sources de données**, cliquez sur un élément faisant partie d'une source de données que vous avez ajoutée à la fenêtre, puis cliquez sur le menu déroulant de l'élément.  
  
3.  Dans le menu déroulant, cliquez sur **Personnaliser**.  L'une des boîtes de dialogue suivantes s'ouvre :  
  
    -   Si le Concepteur Windows Forms est ouvert, la page **Personnalisation de l'interface utilisateur du formulaire de données** de la boîte de dialogue **Options** s'ouvre.  
  
    -   Si le Concepteur WPF est ouvert, la boîte de dialogue **Personnaliser la liaison de contrôles** s'ouvre.  
  
4.  Dans la boîte de dialogue, sélectionnez un type de données dans la liste déroulante **Type de données**.  
  
    -   Pour personnaliser la liste de contrôles d'une table ou d'un objet, sélectionnez **\[Liste\]**.  
  
    -   Pour personnaliser la liste de contrôles d'une colonne de table ou d'une propriété d'objet, sélectionnez le type de données de la colonne ou de la propriété dans le magasin de données sous\-jacent.  
  
    -   Pour personnaliser la liste de contrôles afin d'afficher des objets de données ayant des formes définies par l'utilisateur, sélectionnez **\[Autre\]**.  Par exemple, sélectionnez **\[Autre\]** si votre application possède un contrôle personnalisé qui affiche des données provenant de plusieurs propriétés d'un objet particulier.  
  
5.  Dans la zone **Contrôles associés**, sélectionnez chaque contrôle que vous souhaitez rendre disponible pour le type de données sélectionné ou effacez la sélection des contrôles que vous souhaitez supprimer de la liste.  
  
    > [!NOTE]
    >  Si le contrôle que vous souhaitez sélectionner ne s'affiche pas dans la zone **Contrôles associés**, vous devez ajouter le contrôle à la liste.  Pour plus d'informations, consultez [Ajout de contrôles à la liste des contrôles associés à un type de données](#addingcontrols).  
  
6.  Cliquez sur **OK**.  
  
7.  Dans la fenêtre **Sources de données**, cliquez sur un élément du type de données auquel vous venez d'associer un ou plusieurs contrôles, puis cliquez sur le menu déroulant de l'élément.  
  
     Les contrôles que vous avez sélectionnés dans la zone **Contrôles associés** s'affichent à présent dans le menu déroulant de l'élément.  
  
##  <a name="addingcontrols"></a> Ajout de contrôles à la liste des contrôles associés à un type de données  
 Si vous souhaitez associer un contrôle à un type de données, mais que le contrôle ne s'affiche pas dans la zone **Contrôles associés**, vous devez ajouter le contrôle à la liste.  Le contrôle doit se trouver dans la solution actuelle ou dans un assembly référencé, être disponible dans la **Boîte à outils** et comporter un attribut qui spécifie le comportement de liaison de données du contrôle.  
  
#### Pour ajouter des contrôles à la liste des contrôles associés  
  
1.  Ajoutez le contrôle souhaité à la **Boîte à outils** en cliquant avec le bouton droit sur celle\-ciet en sélectionnant **Choisir les éléments**.  
  
     Le contrôle doit comporter l'un des attributs suivants.  
  
    |Attribut|Description|  
    |--------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implémentez cet attribut sur des contrôles simple qui affichent une colonne \(ou propriété\) unique de données, tels que <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implémentez cet attribut sur des contrôles qui affichent des listes \(ou des tables\) de données, tels que <xref:System.Windows.Forms.DataGridView>.|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implémentez cet attribut sur des contrôles qui affichent des listes \(ou des tables\) de données, mais doivent également présenter une colonne ou une propriété unique, tels que <xref:System.Windows.Forms.ComboBox>.|  
  
2.  Ouvrez la page **Personnalisation de l'interface utilisateur du formulaire de données** de la boîte de dialogue **Options** \(pour Windows Forms\) ou ouvrez la boîte de dialogue **Personnaliser la liaison de contrôles** \(pour WPF\).  Pour plus d'informations, consultez [Personnalisation de la liste des contrôles pouvant être liés pour un type de données](#customizinglist).  
  
3.  Dans la zone **Contrôles associés**, le contrôle que vous venez d'ajouter à la **Boîte à outils** doit maintenant apparaître.  
  
    > [!NOTE]
    >  Seuls les contrôles qui se trouvent dans la solution actuelle ou dans un assembly référencé \(et qui implémentent l'un des attributs de liaison de données dans la table précédente\) peuvent être ajoutés à la liste de contrôles associés.  Pour lier des données à un contrôle personnalisé non disponible dans la fenêtre **Sources de données**, faites glisser le contrôle de la **Boîte à outils** sur l'aire de conception, puis faites glisser l'élément avec lequel effectuer la liaison de la fenêtre **Sources de données** sur le contrôle.  
  
## Voir aussi  
 [Procédure pas à pas : affichage de données sur un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données simple](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)   
 [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données complexe](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)   
 [Procédure pas à pas : création d'un contrôle utilisateur Windows Forms prenant en charge la liaison de données de recherche](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)   
 [Personnaliser la liaison de contrôles, boîte de dialogue](../data-tools/customize-control-binding-dialog-box.md)