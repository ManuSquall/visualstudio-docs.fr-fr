---
title: "Comment&#160;: &#233;tablir une connexion &#224; des donn&#233;es d&#39;une base de donn&#233;es | Microsoft Docs"
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
  - "données (Visual Studio), connecter à des bases de données"
  - "sources de données, créer"
  - "sources de données, bases de données"
  - "connexions de base de données"
  - "bases de données, connecter à"
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
caps.handback.revision: 55
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Comment&#160;: &#233;tablir une connexion &#224; des donn&#233;es d&#39;une base de donn&#233;es
Vous pouvez utiliser Visual Studio pour connecter votre application à une base de données.  Après avoir créé la connexion de données, Visual Studio génère un modèle de données que votre application utilise pour interagir avec les données figurant dans la base de données.  Les objets dans le modèle de données s'affichent dans la [Sources de données \(fenêtre\)](../Topic/Data%20Sources%20Window.md).  Vous pouvez ensuite créer des contrôles liés aux données en faisant glisser des éléments de la fenêtre **Sources de données** vers une aire de conception.  Pour plus d'informations, consultez [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Cette rubrique fournit des instructions pour la connexion à une base de données et la création des types de modèles de données suivants :  
  
-   Groupe de données  
  
-   EDM \(Entity Data Model\)  
  
> [!NOTE]
>  Vous pouvez également utiliser Visual Studio pour créer des classes LINQ to SQL à partir d'une base de données.  Toutefois, les classes LINQ to SQL ne s'affichent pas dans la fenêtre **Sources de données**, il n'est donc pas possible de les faire glisser directement vers un concepteur pour créer des contrôles liés aux données.  Pour plus d'informations sur la création de classes LINQ to SQL à partir d'une base de données, consultez [Procédure : créer des classes LINQ to SQL mappées à des tables et à des vues \(Concepteur O\/R\)](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
##  <a name="dataset"></a> Connexion à une base de données et création d'un groupe de données  
 Lorsque vous créez un groupe de données basé sur une base de données, Visual Studio crée un ensemble de classes qui représente une vue programmable des données.  La classe principale est appelée *dataset typé*.  Le dataset typé contient des objets de table de données qui représentent des tables dans la base de données.  Pour plus d'informations sur les datasets typés, consultez [Utilisation de groupes de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
 Après avoir créé un groupe de données \(dataset\), vous pouvez créer des contrôles WPF ou des contrôles Windows Forms liés aux données en faisant glisser des objets Dataset de la fenêtre Sources de données vers le Concepteur WPF ou le Concepteur Windows Forms.  
  
#### Pour connecter votre application à une base de données et créer un groupe de données  
  
1.  Ouvrez un projet existant dans Visual Studio ou créez un nouveau projet.  
  
2.  Dans le menu **Données**, cliquez sur **Ajouter une nouvelle source de données**.  
  
     L'**Assistant Configuration de source de données** s'ouvre.  
  
3.  Dans la page **Choisir un type de source de données**, sélectionnez **Base de données**, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Choisir un modèle de base de données**, sélectionnez **Groupe de données**, puis cliquez sur **Suivant**.  
  
5.  Sur la page **Choisir votre connexion de données**, sélectionnez une connexion de données dans la liste de connexions disponibles, puis cliquez sur **Suivant**.  
  
     Si la connexion de données souhaitée n'est pas disponible, créez une nouvelle connexion en suivant les étapes dans [Création d'une nouvelle connexion à une base de données](#CreatingDataConnection).  
  
6.  Sur la page **Enregistrer la chaîne de connexion dans le fichier de configuration de l'application**, désactivez éventuellement la case à cocher **Oui, enregistrez la connexion en tant que** si vous souhaitez enregistrer directement la chaîne de connexion dans l'application compilée.  Par défaut, la connexion est enregistrée dans le fichier de configuration de l'application.  Pour plus d'informations, consultez [Comment : enregistrer et modifier des chaînes de connexion](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
7.  Sur la page **Choisir vos objets de base de données**, sélectionnez les objets de base de données que vous utiliserez dans votre application.  Vous avez également la possibilité de remplacer le **Nom du DataSet** par défaut.  
  
8.  Cliquez sur **Terminer**.  Le groupe de données que vous venez de créer est maintenant disponible dans la fenêtre **Sources de données**.  
  
    > [!NOTE]
    >  Si la fenêtre **Sources de données** n'est pas ouverte, cliquez sur **Afficher les sources de données** dans le menu **Données** pour l'ouvrir.  
  
9. Vous pouvez maintenant faire glisser des éléments de la fenêtre **Sources de données** vers le Concepteur WPF, le Concepteur Windows Forms ou le [Component Designer](../Topic/Component%20Designer.md) pour créer des contrôles liés aux données.  Pour plus d'informations, consultez [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
##  <a name="edm"></a> Connexion à la base de données et création d'un Entity Data Model  
 Lorsque vous créez un Entity Data Model basé sur une base de données, Visual Studio crée un ensemble de classes qui représente une vue programmable des données.  Pour plus d'informations sur les Entity Data Models et ADO.NET Entity Framework, consultez [Vue d'ensemble d'Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
 Après avoir créé un Entity Data Model, vous pouvez créer des contrôles WPF liés aux données en faisant glisser des objets d'entité de la fenêtre Sources de données vers le Concepteur WPF.  
  
#### Pour connecter votre application à une base de données et créer un Entity Data Model  
  
1.  Ouvrez un projet existant dans Visual Studio ou créez un nouveau projet.  
  
2.  Suivez les étapes de l'**Assistant EDM** pour vous connecter à une base de données et spécifier le contenu du modèle.  Pour plus d'informations, consultez [How to: Create a New .edmx File](http://msdn.microsoft.com/fr-fr/beb8189e-e51c-4051-839c-9902c224abf2).  
  
3.  Au terme de l'**Assistant EDM**, l'Entity Data Model que vous avez créé s'ouvre dans l'Entity Data Model Designer, et les objets de données sont alors disponibles dans la fenêtre **Sources de données**.  
  
    > [!NOTE]
    >  Si la fenêtre **Sources de données** n'est pas ouverte, cliquez sur **Afficher les sources de données** dans le menu **Données** pour l'ouvrir.  
  
4.  Si le Concepteur WPF est ouvert, vous pouvez maintenant faire glisser des éléments de la fenêtre **Sources de données** vers le concepteur pour créer des contrôles liés à l'Entity Data Model.  Pour plus d'informations, consultez [Comment : lier des contrôles WPF à des données dans Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md).  
  
     Si le Concepteur Windows Forms est ouvert, vous ne pouvez pas faire glisser d'éléments de la fenêtre **Sources de données** vers le concepteur.  Pour créer des contrôles liés à l'Entity Data Model, vous devez générer le projet, ajouter une nouvelle source de données d'objet basée sur l'Entity Data Model, puis faire glisser ces objets vers le concepteur.  
  
##  <a name="CreatingDataConnection"></a> Création d'une nouvelle connexion à une base de données  
 Lorsque vous utilisez l'**Assistant Configuration de source de données** ou l'**Assistant EDM**, vous devez spécifier une connexion à la base de données que vous souhaitez utiliser.  Si vous ne disposez pas encore de connexion à la base de données, exécutez les étapes suivantes pour créer la connexion.  
  
 Ces instructions supposent que vous avez déjà démarré l'**Assistant Configuration de source de données** ou l'**Assistant EDM** tel que décrit dans [Connexion à une base de données et création d'un groupe de données](#dataset) et [Connexion à une base de données et création d'un Entity Data Model](#edm).  
  
#### Pour créer une nouvelle connexion à une base de données  
  
1.  Sur la page **Choisir votre connexion de données** de l'**Assistant Configuration de source de données** ou de l'**Assistant EDM**, cliquez sur **Nouvelle connexion**.  
  
     L'une des actions suivantes se produit :  
  
    -   Si vous avez déjà créé une connexion de données dans Visual Studio, la boîte de dialogue **Ajouter une connexion** s'ouvre.  
  
    -   S'il s'agit de la première connexion de données que vous avez créé dans Visual Studio, la boîte de dialogue **Choisir la source de données** s'affiche.  Sélectionnez le type de base de données auquel vous souhaitez vous connecter, puis cliquez sur **OK** pour afficher la boîte de dialogue **Ajouter une connexion**.  
  
2.  Dans la boîte de dialogue **Ajouter une connexion**, entrez les informations demandées.  La boîte de dialogue **Ajouter une connexion** est différente pour chaque type de fournisseur de données.  
  
    > [!NOTE]
    >  Si la **Source de données** sélectionnée dans la boîte de dialogue **Ajouter une connexion** n'est pas la source de données à laquelle vous souhaitez vous connecter, cliquez sur **Modifier** pour ouvrir la boîte de dialogue **Modifier la source de données**, puis choisir une source de données différente.  
  
3.  Dans la boîte de dialogue **Ajouter une connexion**, cliquez sur **OK**.  
  
     Vous revenez à la page **Choisir votre connexion de données** de l'**Assistant Configuration de source de données** ou de l'**Assistant EDM**.  
  
4.  Sur la page **Choisir votre connexion de données**, assurez\-vous que la nouvelle connexion de données est sélectionnée puis cliquez sur **Suivant**.  
  
5.  Complétez les étapes restantes dans l'**Assistant Configuration de source de données** ou de l'**Assistant EDM**.  
  
## Sécurité .NET Framework  
 Le stockage d'informations sensibles \(telles qu'un mot de passe\) peut affecter la sécurité de votre application.  L'utilisation de l'authentification Windows \(également appelée sécurité intégrée\) offre un moyen plus sûr de contrôler l'accès à une base de données.  Pour plus d'informations, consultez [Protection des informations de connexion](../Topic/Protecting%20Connection%20Information.md).  
  
## Voir aussi  
 [Vue d'ensemble des sources de données](../data-tools/add-new-data-sources.md)   
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Connexion à une source de données](../Topic/Connecting%20to%20a%20Data%20Source%20in%20ADO.NET.md)