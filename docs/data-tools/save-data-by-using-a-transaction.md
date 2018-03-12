---
title: "Comment : enregistrer des données à l’aide d’une transaction | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 9f2373e3a851899d139360caf0f6bb8b6ab0efa5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Comment : enregistrer des données à l’aide d’une transaction
Vous enregistrez des données dans une transaction à l’aide de la <xref:System.Transactions> espace de noms. Utilisez le <xref:System.Transactions.TransactionScope> objet de participer à une transaction qui est gérée automatiquement pour vous.  
  
Projets ne sont pas créés avec une référence à l’assembly System.Transactions, donc vous devez ajouter manuellement une référence aux projets qui utilisent des transactions.  
  
Le moyen le plus simple d’implémenter une transaction consiste à instancier un <xref:System.Transactions.TransactionScope> de l’objet dans un `using` instruction. (Pour plus d’informations, consultez [à l’aide de l’instruction](/dotnet/visual-basic/language-reference/statements/using-statement), et [à l’aide d’instruction](/dotnet/csharp/language-reference/keywords/using-statement).) Le code qui s’exécute dans le `using` instruction participe à la transaction.  
  
Pour valider la transaction, appelez le <xref:System.Transactions.TransactionScope.Complete%2A> bloquer de la dernière instruction à l’aide de la méthode.  
  
Pour restaurer la transaction, levez une exception avant d’appeler le <xref:System.Transactions.TransactionScope.Complete%2A> (méthode).  
  
## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Pour ajouter une référence à la System.Transactions.dll.  
  
1.  Sur le **projet** menu, sélectionnez **ajouter une référence**.  
  
2.  Sur le **.NET** onglet (**SQL Server** onglet pour les projets SQL Server), sélectionnez **System.Transactions**, puis sélectionnez **OK**.  
  
     Une référence à System.Transactions.dll est ajoutée au projet.  
  
## <a name="to-save-data-in-a-transaction"></a>Pour enregistrer les données dans une transaction  
  
-   Ajoutez le code pour enregistrer des données dans à l’aide de l’instruction qui contient la transaction. Le code suivant montre comment créer et instancier une <xref:System.Transactions.TransactionScope> objet à l’aide d’une instruction :  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## <a name="see-also"></a>Voir aussi
[Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)  
[Procédure pas à pas : enregistrer des données dans une transaction](../data-tools/save-data-in-a-transaction.md)  