---
title: "Comment&#160;: ajouter du code aux groupes de donn&#233;es dans des applications multicouches | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "applications multicouches, étendre des groupes de données"
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 20
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: ajouter du code aux groupes de donn&#233;es dans des applications multicouches
Vous pouvez étendre les fonctionnalités d'un groupe de données en créant un fichier de classe partielle pour le groupe de données et en y ajoutant du code \(au lieu d'ajouter du code au fichier *NomGroupeDonnées*Dataset.Designer\).  Les classes partielles permettent de répartir du code parmi plusieurs fichiers physiques pour une classe spécifique.  Pour plus d'informations, consultez [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) ou [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).\)  
  
 Le code qui définit un groupe de données est généré à chaque fois que des modifications sont apportées à la définition du groupe de données \(dans le [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)\).  Ce code est également généré lorsque vous apportez des modifications pendant l'exécution de n'importe quel Assistant qui modifie la configuration d'un groupe de données.  Pour empêcher la suppression de votre code pendant la régénération d'un groupe de données, ajoutez le code au fichier de classe partielle de ce dernier.  
  
 Par défaut, une fois que vous avez séparé le code du groupe de données et le code du `TableAdapter`, vous obtenez un fichier de classe discret dans chaque projet.  Le projet d'origine a un fichier nommé *NomGroupeDonnées*.Designer.vb \(ou *NomGroupeDonnées*.Designer.cs\) qui contient le code du `TableAdapter`.  Le projet désigné dans la propriété **Projet DataSet** a un fichier nommé *NomGroupeDonnées*.DataSet.Designer.vb \(ou *NomGroupeDonnées*.DataSet.Designer.cs\) qui contient le code du groupe de données.  
  
> [!NOTE]
>  Lorsque vous séparez des groupes de données et des `TableAdapter`s \(en définissant la propriété **Projet DataSet**\), les classes DataSet partielles existant dans le projet ne sont pas automatiquement déplacées.  En effet, ces classes doivent être déplacées manuellement vers le projet DataSet.  
  
> [!NOTE]
>  Le [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md) propose également des fonctionnalités pour générer les gestionnaires d'événements <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging> lorsque le code de validation doit être ajouté.  Pour plus d'informations, consultez [Comment : ajouter la validation à un groupe de données multicouche](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
### Pour ajouter du code aux groupes de données dans des applications multicouches  
  
1.  Localisez le projet qui contient le fichier .xsd \(le [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)\).  
  
2.  Double\-cliquez sur le fichier **.xsd** pour ouvrir le [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Cliquez avec le bouton droit sur la table de données dans laquelle vous souhaitez ajouter le code \(le nom de table dans la barre de titre\) et cliquez sur **Afficher le code**.  
  
     Une classe partielle est créée et s'ouvre dans l'éditeur de code.  
  
4.  Ajoutez le code à l'intérieur de la déclaration de classe partielle.  
  
     L'exemple suivant indique où ajouter le code au CustomersDataTable dans NorthwindDataSet :  
  
    ```vb#  
    Partial Public Class CustomersDataTable  
        ' Add code here to add functionality   
        ' to the CustomersDataTable.  
    End Class  
    ```  
  
    ```c#  
    partial class CustomersDataTable  
    {  
        // Add code here to add functionality  
        // to the CustomersDataTable.  
    }  
    ```  
  
## Voir aussi  
 [Vue d'ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md)   
 [Comment : ajouter du code aux TableAdapters dans des applications multicouches](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Vue d'ensemble de TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Vue d'ensemble de la mise à jour hiérarchique](../Topic/Hierarchical%20Update%20Overview.md)   
 [Création d'applications de données](../data-tools/creating-data-applications.md)   
 [Utilisation de groupes de données dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)