---
title: "Comment&#160;: enregistrer des donn&#233;es &#224; l&#39;aide d&#39;une transaction | Microsoft Docs"
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
  - "données (Visual Studio), enregistrer"
  - "enregistrer les données, à l'aide de transactions"
  - "System.Transactions (espace de noms)"
  - "transactions, enregistrer les données"
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comment&#160;: enregistrer des donn&#233;es &#224; l&#39;aide d&#39;une transaction
Vous pouvez enregistrer des données dans une transaction à l'aide de l'espace de noms <xref:System.Transactions>.  Utilisez l'objet <xref:System.Transactions.TransactionScope> pour participer à une transaction qui est gérée automatiquement pour vous.  
  
 Les projets n'étant pas créés avec une référence à l'assembly System.Transactions,  vous devez ajouter manuellement une référence aux projets qui utilisent des transactions.  
  
> [!NOTE]
>  L'espace de noms <xref:System.Transactions> est pris en charge sur Windows 2000 et versions ultérieures.  
  
 La façon la plus facile d'implémenter une transaction consiste à instancier un objet <xref:System.Transactions.TransactionScope> dans une instruction `using`.  \(Pour plus d'informations, consultez [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement) et [using, instruction](/dotnet/csharp/language-reference/keywords/using-statement).\) Le code exécuté au sein de l'instruction `using` participera à la transaction.  
  
 Pour valider la transaction, appelez la méthode <xref:System.Transactions.TransactionScope.Complete%2A> en tant que dernière instruction dans le bloc using.  
  
 Pour restaurer la transaction, levez une exception avant d'appeler la méthode <xref:System.Transactions.TransactionScope.Complete%2A>.  
  
 Pour plus d'informations, consultez [Procédure pas à pas : enregistrement de données dans une transaction](../data-tools/save-data-in-a-transaction.md).  
  
### Pour ajouter une référence à la DLL System.Transactions  
  
1.  Dans le menu **Projet**, sélectionnez **Ajouter une référence**.  
  
2.  Sélectionnez **System.Transactions** sous l'onglet **.NET** \(onglet **SQL Server** pour les projets SQL Server\) et cliquez sur **OK**.  
  
     Une référence à System.Transactions.dll est ajoutée au projet.  
  
### Pour enregistrer des données dans une transaction  
  
-   Ajoutez le code pour enregistrer des données dans l'instruction using qui contient la transaction.  Le code suivant indique comment créer et instancier un objet <xref:System.Transactions.TransactionScope> dans une instruction using :  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## Voir aussi  
 [Procédure pas à pas : enregistrement de données dans une transaction](../data-tools/save-data-in-a-transaction.md)   
 [Liaison de contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Vue d'ensemble d'applications de données dans Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Préparation de votre application pour recevoir des données](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Extraction de données dans votre application](../data-tools/fetching-data-into-your-application.md)   
 [Liaison de contrôles à des données dans Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modification des données dans votre application](../data-tools/editing-data-in-your-application.md)   
 [Validation des données](../Topic/Validating%20Data.md)   
 [Enregistrement des données](../data-tools/saving-data.md)