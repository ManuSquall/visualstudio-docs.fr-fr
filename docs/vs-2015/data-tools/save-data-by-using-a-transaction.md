---
title: Enregistrer les données à l’aide d’une transaction | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b93c512bafd8b15682ed081c7778660ef52fd1f7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692499"
---
# <a name="save-data-by-using-a-transaction"></a>Enregistrer des données à l’aide d’une transaction
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous enregistrez des données dans une transaction en utilisant le <xref:System.Transactions> espace de noms. Utilisez le <xref:System.Transactions.TransactionScope> objet de participer à une transaction qui est gérée automatiquement pour vous.  
  
 Projets ne sont pas créés avec une référence à l’assembly System.Transactions, donc vous devez ajouter manuellement une référence aux projets qui utilisent des transactions.  
  
> [!NOTE]
> Le <xref:System.Transactions> espace de noms est prise en charge dans Windows 2000 ou version ultérieure.  
  
 Le moyen le plus simple d’implémenter une transaction consiste à instancier un <xref:System.Transactions.TransactionScope> de l’objet dans un `using` instruction. (Pour plus d’informations, consultez [Using, instruction](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1), et [à l’aide d’instruction](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) Le code qui s’exécute dans le `using` instruction participe à la transaction.  
  
 Pour valider la transaction, appelez le <xref:System.Transactions.TransactionScope.Complete%2A> bloquer la dernière instruction dans l’à l’aide de la méthode.  
  
 Pour restaurer la transaction, lève une exception avant d’appeler le <xref:System.Transactions.TransactionScope.Complete%2A> (méthode).  
  
 Pour plus d’informations, consultez [enregistrer des données dans une transaction](../data-tools/save-data-in-a-transaction.md).  
  
### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>Pour ajouter une référence à la dll System.Transactions  
  
1. Sur le **projet** menu, sélectionnez **ajouter une référence**.  
  
2. Sur le **.NET** onglet (**SQL Server** onglet pour les projets SQL Server), sélectionnez **System.Transactions**, puis sélectionnez **OK**.  
  
     Une référence à System.Transactions.dll est ajoutée au projet.  
  
### <a name="to-save-data-in-a-transaction"></a>Pour enregistrer les données dans une transaction  
  
- Ajoutez du code pour enregistrer des données dans à l’aide de l’instruction qui contient la transaction. Le code suivant montre comment créer et instancier un <xref:System.Transactions.TransactionScope> objet dans un à l’aide de déclaration :  
  
     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
