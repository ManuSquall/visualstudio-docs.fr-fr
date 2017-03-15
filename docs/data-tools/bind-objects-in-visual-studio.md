---
title: "Liaison d&#39;objets dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "liaison, à des objets"
  - "données (Visual Studio), lier à des objets"
  - "données (Visual Studio), liaison d'objet"
  - "liaison d'objet"
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Liaison d&#39;objets dans Visual Studio
Visual Studio fournit des outils de conception pour l'utilisation d'objets personnalisés \(par opposition à d'autres sources de données telles que les entités, les groupes de données et les services\) comme source de données dans votre application.  
  
## Spécifications des objets  
 La seule condition indispensable au bon fonctionnement des objets personnalisés avec les outils de conception de données dans Visual Studio est que l'objet possède au moins une propriété publique.  
  
 Généralement, les objets personnalisés ne requièrent pas que des interfaces, constructeurs ou attributs spécifiques jouent le rôle de source de données pour une application.  Toutefois, si vous souhaitez faire glisser l'objet de la fenêtre **Sources de données** vers une aire de conception pour créer un contrôle lié aux données, et si l'objet implémente l'interface <xref:System.ComponentModel.ITypedList> ou <xref:System.ComponentModel.IListSource>, l'objet doit disposer d'un constructeur par défaut \(autrement dit, un constructeur sans paramètre\).  Si ce n'est pas le cas, Visual Studio ne peut pas instancier l'objet source de données et affiche une erreur lorsque vous faites glisser l'élément sur l'aire de conception.  
  
## Exemples d'utilisation d'objets personnalisés comme sources de données  
 Bien qu'il existe d'innombrables façons d'implémenter votre logique d'application lors de l'utilisation d'objets comme source de données, seules quelques opérations standard peuvent être simplifiées à l'aide des objets [TableAdapter](../data-tools/tableadapter-overview.md) générés par Visual Studio.  Cette page explique comment implémenter ces processus standard à l'aide de TableAdapters ; elle n'est pas conçue comme un guide pour créer vos objets personnalisés.  Par exemple, vous exécutez généralement les opérations standard suivantes indépendamment de l'implémentation spécifique de vos objets ou de la logique de l'application :  
  
-   Chargement de données dans des objets \(généralement à partir d'une base de données\).  
  
-   Création d'une collection typée d'objets.  
  
-   Ajout et suppression d'objets dans une collection.  
  
-   Affichage des données d'objet pour les utilisateurs sur un formulaire.  
  
-   Modification des données dans un objet.  
  
-   Réenregistrement des données provenant d'objets dans la base de données.  
  
> [!NOTE]
>  Pour mieux comprendre et fournir le contexte pour les exemples de cette page, nous vous suggérons d'effectuer la procédure suivante : [Procédure pas à pas : connexion à des données dans des objets \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  Cette procédure pas à pas crée les objets présentés sur cette page d'aide.  
  
### Chargement de données dans des objets  
 Pour cet exemple, vous chargez des données dans vos objets à l'aide de TableAdapters.  Par défaut, les TableAdapters sont créés avec deux types de méthodes qui extraient les données d'une base de données et remplissent des tables de données.  
  
-   La méthode `TableAdapter.Fill` remplit une table de données existante avec les données retournées.  
  
-   La méthode `TableAdapter.GetData` retourne une nouvelle table de données remplie avec les données.  
  
 La façon la plus facile de charger vos objets personnalisés avec les données consiste à appeler la méthode `TableAdapter.GetData`, parcourir la collection de lignes dans la table de données retournée et remplir chaque objet avec les valeurs dans chaque ligne.  Vous pouvez créer une méthode `GetData` qui retourne une table de données remplie pour toute requête ajoutée à un TableAdapter.  
  
> [!NOTE]
>  Visual Studio nomme les requêtes TableAdapter `Fill` et `GetData` par défaut, mais ces noms peuvent être modifiés en noms de méthodes valides.  
  
 L'exemple suivant indique comment parcourir les lignes d'une table de données et remplir un objet avec les données :  
  
 Pour obtenir un exemple de code complet, consultez [Procédure pas à pas : connexion à des données dans des objets \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
 [!code-cs[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]  
  
### Création d'une collection typée d'objets  
 Vous pouvez créer des classes de collection pour vos objets ou utiliser les collections typées fournies automatiquement par le [Composant BindingSource](../Topic/BindingSource%20Component.md).  
  
 Lorsque vous créez une classe de collection personnalisée pour les objets, nous vous suggérons d'hériter de <xref:System.ComponentModel.BindingList%601>.  Cette classe générique fournit les fonctionnalités destinées à l'administration de votre collection et vous permet de déclencher des événements qui envoient des notifications à l'infrastructure de liaison de données dans Windows Forms.  
  
 La collection générée automatiquement dans <xref:System.Windows.Forms.BindingSource> utilise <xref:System.ComponentModel.BindingList%601> pour sa collection typée.  Si votre application ne nécessite pas de fonctionnalités supplémentaires, vous pouvez conserver votre collection dans <xref:System.Windows.Forms.BindingSource>.  Pour plus d'informations, reportez\-vous à la propriété <xref:System.Windows.Forms.BindingSource.List%2A> de la classe <xref:System.Windows.Forms.BindingSource>.  
  
> [!NOTE]
>  Si votre collection requiert des fonctionnalités non fournies par l'implémentation de base de <xref:System.ComponentModel.BindingList%601>, vous devez créer une collection personnalisée pour pouvoir ajouter à la classe selon les besoins.  
  
 Le code suivant indique comment créer la classe pour une collection fortement typée d'objets `Order` :  
  
 [!code-cs[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]  
  
### Ajout de plusieurs objets à une collection.  
 Vous ajoutez des objets à une collection en appelant la méthode `Add` de votre classe de collection personnalisée ou de <xref:System.Windows.Forms.BindingSource>.  
  
 Pour obtenir un exemple d'ajout de collection à l'aide de <xref:System.Windows.Forms.BindingSource>, consultez la méthode `LoadCustomers` dans [Procédure pas à pas : connexion à des données dans des objets \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
 Pour obtenir un exemple d'ajout d'objets à une collection personnalisée, consultez la méthode `LoadOrders` dans [Procédure pas à pas : connexion à des données dans des objets \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
> [!NOTE]
>  La méthode `Add` est fournie automatiquement pour votre collection personnalisée lorsque vous héritez de <xref:System.ComponentModel.BindingList%601>.  
  
 Le code suivant indique comment ajouter des objets à la collection typée à <xref:System.Windows.Forms.BindingSource> :  
  
 [!code-cs[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]  
  
 Le code suivant indique comment ajouter des objets à une collection typée qui hérite de <xref:System.ComponentModel.BindingList%601> :  
  
> [!NOTE]
>  Dans cet exemple, la collection `Orders` est une propriété de l'objet `Customer`.  
  
 [!code-cs[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]  
  
### Suppression d'objets d'une collection  
 Vous supprimez des objets d'une collection en appelant la méthode `Remove` ou `RemoveAt` de votre classe de collection personnalisée ou de <xref:System.Windows.Forms.BindingSource>.  
  
> [!NOTE]
>  Les méthodes `Remove` et `RemoveAt` sont fournies automatiquement pour votre collection personnalisée lorsque vous héritez de <xref:System.ComponentModel.BindingList%601>.  
  
 Le code suivant indique comment localiser et supprimer des objets de la collection typée dans un <xref:System.Windows.Forms.BindingSource> avec la méthode <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> :  
  
 [!code-cs[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]  
  
### Affichage de données d'objet pour les utilisateurs  
 Pour que les utilisateurs puissent voir les données dans les objets, vous créez une source de données Objet à l'aide de l'[Configuration de source de données \(Assistant\)](../data-tools/media/data-source-configuration-wizard.png), puis faites glisser l'intégralité de l'objet ou des propriétés individuelles sur votre formulaire à partir de la fenêtre **Sources de données**.  
  
 Pour plus d'informations sur la création d'une source de données d'objet, consultez [Comment : se connecter à des données dans des objets](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
 Pour plus d'informations sur l'affichage de données provenant d'objets sur Windows Forms, consultez [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
### Modification des données contenues dans des objets  
 Pour modifier les données contenues dans des objets personnalisés qui sont liés par des données aux contrôles Windows Forms, il vous suffit de modifier les données dans le contrôle associé \(ou directement dans les propriétés de l'objet\).  L'architecture de liaison de données met à jour les données dans l'objet.  
  
 Si votre application nécessite le suivi de modifications et la restauration de modifications proposées à leurs valeurs d'origine, vous devez implémenter ces fonctionnalités dans votre modèle objet.  Pour obtenir des exemples de la façon dont les tables de données suivent les modifications proposées, consultez <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A> et <xref:System.Data.DataTable.GetChanges%2A>.  
  
### Réenregistrement dans la base de données de données contenues dans les objets  
 Vous réenregistrez des données dans la base de données en passant les valeurs provenant de votre objet dans les méthodes DBDirect du TableAdapter.  
  
 Visual Studio crée des méthodes DBDirect qui peuvent être exécutées directement par rapport à la base de données.  Ces méthodes ne requièrent pas d'objets DataSet ou DataTable.  
  
|Méthode DBDirect de TableAdapter|Description|  
|--------------------------------------|-----------------|  
|`TableAdapter.Insert`|Ajoute de nouveaux enregistrements à une base de données, ce qui vous permet de passer des valeurs de colonne individuelles comme paramètres de méthode.|  
|`TableAdapter.Update`|Met à jour des enregistrements existants dans une base de données.  La méthode Update prend des valeurs de colonne nouvelles et d'origine comme paramètres de méthode.  Les valeurs d'origine servent à localiser l'enregistrement d'origine et les nouvelles valeurs à mettre à jour cet enregistrement.<br /><br /> La méthode `TableAdapter.Update` permet également de rapprocher les modifications apportées à un groupe de données dans la base de données en prenant une <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> ou un tableau de <xref:System.Data.DataRow> comme paramètres de méthode.|  
|`TableAdapter.Delete`|Supprime des enregistrements existants de la base de données en fonction des valeurs de colonne transmises en tant que paramètres de méthode.|  
  
 Pour enregistrer des données provenant d'une collection d'objets, parcourez la collection d'objets \(par exemple, à l'aide d'une boucle for\-next\) et envoyez les valeurs pour chaque objet à la base de données à l'aide des méthodes DBDirect du TableAdapter.  
  
 L'exemple suivant indique comment utiliser la méthode `TableAdapter.Insert` DBDirect pour ajouter un nouveau client directement dans la base de données :  
  
 [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]  
  
## Voir aussi  
 [Comment : se connecter à des données dans des objets](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [Procédure pas à pas : connexion à des données dans des objets \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [Comment : enregistrer les données d'un objet dans une base de données](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Comment : accéder directement à la base de données avec un TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [Procédure pas à pas : enregistrement des données avec les méthodes DBDirect du TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Enregistrement des données](../data-tools/saving-data.md)