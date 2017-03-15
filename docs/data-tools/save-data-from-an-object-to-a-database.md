---
title: "Comment&#160;: enregistrer les donn&#233;es d&#39;un objet dans une base de donn&#233;es | Microsoft Docs"
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
  - "données (Visual Studio), enregistrer"
  - "accès aux données (Visual Studio), objets"
  - "enregistrer les données"
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 9
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: enregistrer les donn&#233;es d&#39;un objet dans une base de donn&#233;es
Vous pouvez enregistrer dans une base de données les données contenues dans un objet en passant les valeurs de votre objet à l'une des méthodes DBDirect \(par exemple, `TableAdapter.Insert`\) du TableAdapter.  Pour plus d'informations, consultez [Vue d'ensemble de TableAdapter](../data-tools/tableadapter-overview.md).  
  
 Pour enregistrer des données provenant d'une collection d'objets, parcourez la collection d'objets \(par exemple, une boucle for\-next\) et envoyez les valeurs pour chaque objet à la base de données à l'aide de l'une des méthodes DBDirect du TableAdapter.  
  
 Par défaut, les méthodes DBDirect sont créées sur un TableAdapter qui peut être exécuté directement par rapport à la base de données.  Ces méthodes peuvent être appelées directement et ne nécessitent aucun objet <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> pour rapprocher des modifications pour envoyer des mises à jour à une base de données.  
  
> [!NOTE]
>  Lorsque vous configurez un TableAdapter, la requête principale doit fournir assez d'informations pour la création des méthodes DBDirect.  Par exemple, si un TableAdapter est configuré pour interroger les données d'une table qui n'a pas de colonne de clé primaire définie, il ne génère pas de méthodes DBDirect.  
  
|Méthode DBDirect de TableAdapter|Description|  
|--------------------------------------|-----------------|  
|`TableAdapter.Insert`|Ajoute de nouveaux enregistrements à une base de données, ce qui vous permet de passer des valeurs de colonne individuelles comme paramètres de méthode.|  
|`TableAdapter.Update`|Met à jour des enregistrements existants dans une base de données.  La méthode `Update` prend des valeurs de colonne nouvelles et d'origine comme paramètres de méthode.  Les valeurs d'origine servent à localiser l'enregistrement d'origine et les nouvelles valeurs à mettre à jour cet enregistrement.<br /><br /> La méthode `TableAdapter.Update` permet également de rapprocher les modifications apportées à un groupe de données dans la base de données en prenant une <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> ou un tableau de <xref:System.Data.DataRow> comme paramètres de méthode.|  
|`TableAdapter.Delete`|Supprime des enregistrements existants de la base de données en fonction des valeurs de colonne transmises en tant que paramètres de méthode.|  
  
### Pour enregistrer de nouveaux enregistrements provenant d'un objet dans une base de données  
  
-   Créez les enregistrements en passant les valeurs à la méthode `TableAdapter.Insert`.  
  
     L'exemple suivant crée un enregistrement client dans la table `Customers` en passant les valeurs dans l'objet `currentCustomer` à la méthode `TableAdapter.Insert`.  
  
     [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]  
  
### Pour mettre à jour des enregistrements existants provenant d'un objet dans une base de données  
  
-   Modifiez les enregistrements en appelant la méthode `TableAdapter.Update` et en passant les nouvelles valeurs pour mettre à jour l'enregistrement et en passant les valeurs d'origine pour localiser l'enregistrement.  
  
    > [!NOTE]
    >  Votre objet doit conserver les valeurs d'origine pour les passer à la méthode `Update`.  Cet exemple utilise des propriétés avec un préfixe `orig` pour stocker les valeurs d'origine.  
  
     L'exemple suivant met à jour un enregistrement existant dans la table `Customers` en passant les valeurs nouvelles et d'origine dans l'objet `Customer` à la méthode `TableAdapter.Update`.  
  
     [!code-cs[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]  
  
### Pour supprimer des enregistrements existants d'une base de données  
  
-   Supprimez les enregistrements en appelant la méthode `TableAdapter.Delete` et en passant les valeurs d'origine pour localiser l'enregistrement.  
  
    > [!NOTE]
    >  Votre objet doit conserver les valeurs d'origine pour les passer à la méthode `Delete`.  Cet exemple utilise des propriétés avec un préfixe `orig` pour stocker les valeurs d'origine.  
  
     L'exemple suivant supprime un enregistrement de la table `Customers` en passant les valeurs d'origine dans l'objet `Customer` à la méthode `TableAdapter.Delete`.  
  
     [!code-cs[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]  
  
## Sécurité .NET Framework  
 Vous devez avoir l'autorisation pour exécuter les instructions INSERT, UPDATE ou DELETE sur la table dans la base de données.  
  
## Voir aussi  
 [Liaison d'objets dans Visual Studio](../data-tools/bind-objects-in-visual-studio.md)   
 [Comment : se connecter à des données dans des objets](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [Procédure pas à pas : connexion à des données dans des objets \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [Comment : accéder directement à la base de données avec un TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)