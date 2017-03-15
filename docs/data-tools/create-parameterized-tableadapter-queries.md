---
title: "Comment&#160;: cr&#233;er des requ&#234;tes TableAdapter param&#233;tr&#233;es | Microsoft Docs"
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
  - "données (Visual Studio), rechercher les données"
  - "données (Visual Studio), TableAdapters"
  - "requêtes (Visual Studio), créer"
  - "requêtes (Visual Studio), TableAdapters"
  - "TableAdapters, requêtes paramétrables"
  - "TableAdapters, rechercher les données"
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: cr&#233;er des requ&#234;tes TableAdapter param&#233;tr&#233;es
Une requête paramétrable retourne des données remplissant les conditions d'une clause WHERE dans la requête.  Par exemple, vous pouvez paramétrer une liste de clients de sorte à n'afficher que les clients d'une certaine ville en ajoutant `WHERE City = @City` à la fin de l'instruction SQL qui retourne une liste de clients.  
  
 Vous créez des requêtes TableAdapter paramétrables dans le [Concepteur de DataSet](../data-tools/creating-and-editing-typed-datasets.md) ou pendant la création de formulaires liés aux données dans une application Windows avec la commande **Paramétrer la source de données** du menu **Données**.  La commande **Paramétrer la source de données** crée également des contrôles dans votre formulaire pour entrer les valeurs de paramètre et exécuter la requête.  Pour plus d'informations, consultez [Générateur de critères de recherche, boîte de dialogue](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
> [!NOTE]
>  Quand vous construisez une requête paramétrée, utilisez la notation de paramètre propre à la base de données sur laquelle vous encodez.  Par exemple, les sources de données Access et OleDb utilisent le point d'interrogation « ? » pour désigner des paramètres, la clause WHERE sera donc de type : `WHERE City = ?`.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Création d'une requête TableAdapter paramétrée  
  
#### Pour créer une requête paramétrée dans le Concepteur de DataSet  
  
-   Créez un TableAdapter, en ajoutant une clause WHERE avec les paramètres souhaités à l'instruction SQL.  Pour plus d'informations, consultez [Comment : créer des TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
     ou  
  
-   Ajoutez une requête à un TableAdapter existant, en ajoutant une clause WHERE avec les paramètres souhaités à l'instruction SQL.  Pour plus d'informations, consultez [Comment : créer des requêtes TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
#### Pour créer une requête paramétrée pendant la conception d'un formulaire lié aux données  
  
1.  Sélectionnez un contrôle dans votre formulaire déjà lié à un dataset.  Pour plus d'informations, consultez [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
2.  Dans le menu **Données**, cliquez sur **Ajouter une requête**.  
  
3.  Utilisez la boîte de dialogue **Générateur de critères de recherche**, en ajoutant une clause WHERE avec les paramètres souhaités à l'instruction SQL.  Pour plus d'informations, consultez [Générateur de critères de recherche, boîte de dialogue](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
## Voir aussi  
 [TableAdapters](../Topic/TableAdapters.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)   
 [Procédures pas à pas relatives aux données](../Topic/Data%20Walkthroughs.md)