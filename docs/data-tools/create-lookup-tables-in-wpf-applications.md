---
title: "Comment&#160;: cr&#233;er des tables de correspondance dans des applications WPF | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "données (WPF), afficher"
  - "liaison de données, WPF"
  - "afficher les données, WPF"
  - "WPF (WPF), données"
  - "liaison de données WPF (Visual Studio)"
  - "concepteur WPF, liaison de données"
  - "WPF, liaison de données dans Visual Studio"
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: cr&#233;er des tables de correspondance dans des applications WPF
Vous pouvez créer une table de correspondance en faisant glisser le nœud principal d'une table ou d'un objet parent dans la fenêtre **Sources de données** sur un contrôle qui est déjà lié à une colonne ou une propriété dans une table enfant connexe.  La *table de correspondance de terme* \(parfois appelée *liaison de correspondance*\) décrit un contrôle qui affiche les informations d'une table de données en fonction de la valeur d'un champ de clé étrangère dans une autre table.  
  
 Prenons l'exemple d'une table `Orders` dans une base de données des ventes.  Chaque enregistrement contenu dans la table `Orders` comprend un `CustomerID` qui indique le client ayant passé la commande.  Ce `CustomerID` est une clé étrangère qui pointe vers un enregistrement de client dans la table `Customers`.  Lorsque vous affichez une liste de commandes à partir de la table `Orders`, vous pouvez afficher le nom réel des clients plutôt que le `CustomerID`.  Étant donné que le nom du client se trouve dans la table `Customers`, vous devez créer une table de correspondance pour afficher le nom.  La table de correspondance utilise la valeur `CustomerID` dans l'enregistrement `Orders` pour naviguer jusqu'à la relation et retourner le nom de client convivial.  
  
### Pour créer une table de correspondance  
  
1.  Ajoutez l'un des types suivants de sources de données avec les données connexes à votre projet :  
  
    -   Dataset ou Entity Data Model.  Pour plus d'informations, consultez [Comment : établir une connexion à des données d'une base de données](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
    -   Service de données WCF, service WCF ou service Web.  Pour plus d'informations, consultez [Comment : se connecter à des données dans un service](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
    -   Objets.  Pour plus d'informations, consultez [Comment : se connecter à des données dans des objets](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
    > [!NOTE]
    >  Avant de pouvoir créer une table de correspondance, deux tables ou objets connexes doivent exister comme source de données pour le projet.  
  
2.  Ouvrez le **Concepteur WPF** et assurez\-vous qu'il inclut un conteneur étant une cible valide d'opération de déplacement pour les éléments de la fenêtre **Sources de données**.  
  
     Pour plus d'informations sur les cibles de déplacement valides, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
3.  Dans le menu **Données**, cliquez sur **Afficher les sources de données** pour ouvrir la fenêtre **Sources de données**.  
  
4.  Développez les nœuds dans la fenêtre **Sources de données** jusqu'à la table ou l'objet parent et leur table ou objet enfant connexe.  
  
    > [!NOTE]
    >  La table ou l'objet enfant connexe est le nœud qui apparaît comme un nœud enfant développable sous la table ou l'objet parent.  
  
5.  Cliquez sur le menu déroulant du nœud enfant et sélectionnez **Détails**.  
  
6.  Développez le nœud enfant.  
  
7.  Sous le nœud enfant, cliquez sur le menu déroulant de l'élément qui met en relation les données parentes et enfants \(dans l'exemple ci\-dessus, il s'agirait du nœud **CustomerID**\).  Sélectionnez l'un des types suivants de contrôles qui prennent en charge la liaison de correspondance :  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  Si le contrôle **ListBox** ou **ListView** ne s'affiche pas dans la liste, vous pouvez les ajouter à la liste.  Pour plus d'informations, consultez [Définir le contrôle à créer lors d’une opération de glisser\-déplacer à partir de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    -   Tout contrôle personnalisé dérivé de <xref:System.Windows.Controls.Primitives.Selector>  
  
        > [!NOTE]
        >  Pour plus d'informations sur la façon d'ajouter des contrôles personnalisés à la liste de contrôles que vous pouvez sélectionner pour les éléments dans la fenêtre **Sources de données**, consultez [Ajouter des contrôles personnalisés à la fenêtre Sources de données](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
8.  Faites glisser le nœud enfant de la fenêtre **Sources de données** sur un conteneur dans le Concepteur WPF \(dans l'exemple ci\-dessus, le nœud enfant serait **Commandes** \).  
  
     Visual Studio génère du code XAML qui crée des contrôles liés aux données pour chaque élément que vous faites glisser.  Le code XAML ajoute également une nouvelle <xref:System.Windows.Data.CollectionViewSource> pour la table ou l'objet enfant aux ressources de la cible de déplacement.  Pour certaines sources de données, Visual Studio génère également du code permettant de charger des données dans la table ou l'objet enfant.  Pour plus d'informations, consultez [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
9. Faites glisser le nœud parent de la fenêtre **Sources de données** sur le contrôle de liaison de correspondance créé précédemment \(dans l'exemple ci\-dessus, le nœud parent serait le nœud **Clients**\).  
  
     Visual Studio définit des propriétés sur le contrôle pour configurer la liaison de correspondance.  Le tableau suivant répertorie les propriétés que Visual Studio modifie.  Si nécessaire, vous pouvez modifier ces propriétés dans le code XAML ou dans la fenêtre **Propriétés**.  
  
    |Propriété|Explication de la définition|  
    |---------------|----------------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Cette propriété spécifie la collection ou la liaison utilisée pour obtenir les données affichées dans le contrôle.  Visual Studio affecte à cette propriété la <xref:System.Windows.Data.CollectionViewSource> pour les données parentes que vous avez fait glisser sur le contrôle.|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Cette propriété spécifie le chemin d'accès de l'élément de données affiché dans le contrôle.  Visual Studio affecte à cette propriété la première colonne ou propriété des données parentes, après la clé primaire, possédant un type de données chaîne.<br /><br /> Si vous souhaitez afficher une autre colonne ou propriété dans les données parentes, modifiez cette propriété en spécifiant le chemin d'accès d'une autre propriété.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio lie cette propriété à la colonne ou propriété des données enfant que vous avez fait glisser vers le concepteur.  C'est la clé étrangère des données parentes.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio affecte à cette propriété le chemin d'accès de la colonne ou de la propriété des données enfants qui sont la clé étrangère des données parentes.|  
  
## Voir aussi  
 [Liaison de contrôles WPF avec des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Comment : lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Comment : afficher des données connexes dans des applications WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Procédure pas à pas : affichage de données connexes dans une application WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)