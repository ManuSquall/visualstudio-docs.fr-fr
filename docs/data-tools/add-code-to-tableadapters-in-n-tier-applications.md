---
title: "Comment&#160;: ajouter du code aux TableAdapters dans des applications multicouches | Microsoft Docs"
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
  - "applications multicouches, étendre des TableAdapters"
  - "TableAdapters, applications multicouches"
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 19
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: ajouter du code aux TableAdapters dans des applications multicouches
Vous pouvez étendre les fonctionnalités d'un `TableAdapter` en créant un fichier de classe partielle pour le `TableAdapter` et en y ajoutant le code \(au lieu d'ajouter le code au fichier *NomGroupeDonnées*.DataSet.Designer\).  Les classes partielles permettent de répartir du code parmi plusieurs fichiers physiques pour une classe spécifique.  Pour plus d'informations, consultez [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) ou [partiel, Type](/dotnet/csharp/language-reference/keywords/partial-type).\)  
  
 Le code qui définit un `TableAdapter` est généré à chaque fois que des modifications sont apportées au `TableAdapter` \(dans le [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)\).  Ce code est également généré lorsque vous apportez des modifications pendant l'exécution de n'importe quel Assistant qui modifie la configuration d'un `TableAdapter`.  Pour empêcher la suppression de votre code pendant la régénération d'un `TableAdapter`, ajoutez le code au fichier de classe partielle de ce `TableAdapter`.  
  
 Par défaut, une fois que vous avez séparé le code du groupe de données et le code du `TableAdapter`, vous obtenez un fichier de classe discret dans chaque projet.  Le projet d'origine a un fichier nommé *NomGroupeDonnées*.Designer.vb \(ou *NomGroupeDonnées*.Designer.cs\) qui contient le code du `TableAdapter`.  Le projet désigné dans la propriété **Projet DataSet** a un fichier nommé *NomGroupeDonnées*.DataSet.Designer.vb \(ou *NomGroupeDonnées*.DataSet.Designer.cs\) qui contient le code du groupe de données.  
  
> [!NOTE]
>  Lorsque vous séparez des groupes de données et des `TableAdapter`s \(en définissant la propriété **Projet DataSet**\), les classes DataSet partielles existant dans le projet ne sont pas automatiquement déplacées.  En effet, ces classes doivent être déplacées manuellement vers le projet DataSet.  
  
> [!NOTE]
>  Le [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md) propose également des fonctionnalités pour générer les gestionnaires d'événements <xref:System.Data.DataTable.ColumnChanging> et <xref:System.Data.DataTable.RowChanging> lorsque le code de validation doit être ajouté.  Pour plus d'informations, consultez [Comment : ajouter la validation à un groupe de données multicouche](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Pour ajouter le code utilisateur à un TableAdapter dans une application multicouche  
  
1.  Localisez le projet qui contient le fichier .xsd \(le [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md)\).  
  
2.  Double\-cliquez sur le fichier **.xsd** pour ouvrir le [Création et modification de Datasets typés](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Cliquez avec le bouton droit sur le `TableAdapter` auquel vous souhaitez ajouter le code et cliquez sur **Afficher le code**.  
  
     Une classe partielle est créée et s'ouvre dans l'éditeur de code.  
  
4.  Ajoutez le code à l'intérieur de la déclaration de classe partielle.  
  
5.  L'exemple de code suivant indique où le code doit être ajouté dans le `CustomersTableAdapter` du `NorthwindDataSet` :  
  
    ```vb#  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```c#  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## Voir aussi  
 [Vue d'ensemble des applications de données multicouches](../data-tools/n-tier-data-applications-overview.md)   
 [Comment : ajouter du code aux groupes de données dans des applications multicouches](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Vue d'ensemble de TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Vue d'ensemble de la mise à jour hiérarchique](../Topic/Hierarchical%20Update%20Overview.md)   
 [Création d'applications de données](../data-tools/creating-data-applications.md)