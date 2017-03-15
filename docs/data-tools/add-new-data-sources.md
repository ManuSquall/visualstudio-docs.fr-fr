---
title: "Vue d&#39;ensemble des sources de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datasourcefieldspicker"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "données (Visual Studio), sources de données"
  - "sources de données"
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 56
caps.handback.revision: 41
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vue d&#39;ensemble des sources de donn&#233;es
Les sources de données représentent les données disponibles pour votre application.  Plus spécifiquement, les sources de données représentent les données que vous voulez utiliser dans votre application.  Elles peuvent provenir de bases de données \(notamment des fichiers de base de données locaux\), de services et d'objets.  
  
 Les sources de données que vous ajoutez à votre projet sont affichées dans la fenêtre **Sources de données**.  Dans de nombreux cas, vous pouvez faire glisser les sources de données vers des Windows Forms, et vers les Concepteurs WPF et Silverlight, pour créer des contrôles liés aux données sous\-jacentes.  Pour plus d'informations, consultez [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Visual Studio fournit des outils pour la création et la modification de sources de données dans votre application.  Les sources de données dans les projets Visual Studio sont représentées sous la forme d'Entity Data Models, de groupes de données, d'objets proxy retournés par un service, ou d'autres types d'objets, selon les objets retournés par le magasin de données sous\-jacent.  
  
 Vous créez et modifiez des sources de données à l'aide de l'**Assistant Configuration de source de données**.  
  
## Sources de données créées à partir de bases de données  
 Vous pouvez créer une source de données à partir d'une base de données en exécutant l'**Assistant Configuration de source de données** et en sélectionnant le type de source de données **Base de données**.  Pour plus d'informations, consultez [Comment : établir une connexion à des données d'une base de données](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
 Lorsque vous créez une source de données à partir d'une base de données, Visual Studio génère un *modèle de données* et l'ajoute à votre projet.  Un modèle de données est une vue fortement typée et programmable des données sous\-jacentes dans la base de données.  Vous pouvez utiliser Visual Studio pour créer les types de modèles de données suivants :  
  
-   Un modèle conceptuel basé sur le [Entity Data Model](../Topic/Entity%20Data%20Model.md).  Ce type de modèle peut être utilisé par Entity Framework ou des services de données WCF.  Pour plus d’informations, consultez [Vue d'ensemble d'Entity Framework](../Topic/Entity%20Framework%20Overview.md) et [WCF Data Services 4.5](../Topic/WCF%20Data%20Services%204.5.md).  
  
-   Dataset typé.  Pour plus d'informations, consultez [Utilisation de groupes de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
-   Classes LINQ to SQL.  Pour plus d'informations, consultez [LINQ à SQL](../Topic/LINQ%20to%20SQL.md).  
  
    > [!NOTE]
    >  Contrairement aux modèles conceptuels et aux groupes de données basés sur Entity Data Model, les classes LINQ to SQL ne peuvent pas être créées à l'aide de l'**Assistant Configuration de source de données**.  Elles ne s'affichent pas non plus dans la fenêtre **Sources de données**, et par conséquent ne peuvent pas être déplacées vers un concepteur pour créer des contrôles liés aux données.  Toutefois, vous pouvez créer une source de données Objet basée sur les classes LINQ to SQL et faire glisser ces objets vers le concepteur.  Pour plus d'informations, consultez [Procédure : créer des classes LINQ to SQL mappées à des tables et à des vues \(Concepteur O\/R\)](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md).  
  
### Sources de données créées à partir de fichiers de base de données locaux  
 Vous pouvez également créer des sources de données à partir des types de fichiers de base de données suivants : bases de données Access \(fichiers .mdb\), bases de données LocalDB SQL Server Express \(fichiers .mdf\) et bases de données SQL Server Express \(fichiers .mdf\).  Lorsque vous créez des sources de données à partir de ces fichiers de base de données, vous pouvez ajouter directement les fichiers de base de données à votre projet.  Pour plus d'informations, consultez les rubriques suivantes :  
  
-   [Vue d'ensemble des données locales](../data-tools/local-data-overview.md)  
  
-   [Comment : gérer des fichiers de données locaux dans votre projet](../data-tools/how-to-manage-local-data-files-in-your-project.md)  
  
## Sources de données créées à partir de services  
 Vous pouvez créer une source de données à partir d'un service en exécutant l'**Assistant Configuration de source de données** et en sélectionnant le type de source de données **Service**.  Pour plus d'informations, consultez [Comment : se connecter à des données dans un service](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
 Lorsque vous créez une source de données à partir d'un service, Visual Studio ajoute une référence de service à votre projet.  Visual Studio crée également des objets proxy qui correspondent aux objets retournés par le service.  Par exemple, un service qui retourne un groupe de données est représenté dans votre projet sous la forme d'un groupe de données ; un service qui retourne un type spécifique est représenté dans votre projet sous la forme du type retourné.  
  
 Vous pouvez créer une source de données à partir des types de services suivants :  
  
-   Services de données WCF.  Pour plus d'informations, consultez [Vue d'ensemble](../Topic/WCF%20Data%20Services%20Overview.md).  
  
-   Services WCF \(Windows Communication Foundation\).  Pour plus d'informations, consultez [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).  
  
-   Services Web.  Pour plus d'informations, consultez [Not in Build: Introduction to Programming Web Services in Managed Code](http://msdn.microsoft.com/fr-fr/bd8861f3-39e1-4c06-995e-677e007eb961).  
  
    > [!NOTE]
    >  Les éléments qui s'affichent dans la fenêtre **Sources de données** sont dépendants des données retournées par le service.  Il se peut que certains services ne fournissent pas suffisamment d'informations pour permettre à l'**Assistant Configuration de source de données** de créer des objets pouvant être liés.  Par exemple, si le service retourne un dataset non typé, aucun élément ne s'affichera dans la fenêtre **Sources de données** au terme de l'Assistant.  Ceci est dû au fait que les datasets non typés ne fournissent pas de schéma, et par conséquent, l'Assistant ne dispose pas de suffisamment d'informations pour créer la source de données.  
  
## Sources de données créées à partir d'objets  
 Vous pouvez créer une source de données à partir de n'importe quel objet qui expose une ou plusieurs propriétés publiques en exécutant l'**Assistant Configuration de source de données**, puis en sélectionnant le type de source de données **Objet**.  Toutes les propriétés publiques d'un objet sont affichées dans la fenêtre **Sources de données**.  Pour plus d'informations, consultez [Comment : se connecter à des données dans des objets](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
 Pour plus d'informations sur la liaison à des objets, consultez [Liaison d'objets dans Visual Studio](../data-tools/bind-objects-in-visual-studio.md).  
  
## Sources de données créées à partir de listes SharePoint  
 Vous pouvez créer une source de données à partir d'une liste SharePoint en exécutant l'**Assistant Configuration de source de données** et en sélectionnant le type de source de données **SharePoint**.  SharePoint expose des données via [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] ; créer une source de données SharePoint revient ainsi au même que créer une source de données à partir d'un service.  La sélection de l'élément **SharePoint** dans l'**Assistant Configuration de source de données** ouvre la boîte de dialogue **Ajouter une référence de service** où vous vous connectez au service de données SharePoint en pointant sur le serveur SharePoint.  Pour plus d'informations, consultez [Comment : se connecter à des données dans un service](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
## Voir aussi  
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)   
 [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md)   
 [Vue d'ensemble d'applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)