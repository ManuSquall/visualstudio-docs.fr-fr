---
title: Enregistrer des données à l’aide d’une transaction | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85f3584073523e748168faf569aa918ba912fbf8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652832"
---
# <a name="save-data-by-using-a-transaction"></a>Enregistrer des données à l’aide d’une transaction
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous enregistrez des données dans une transaction à l’aide de l' <xref:System.Transactions> espace de noms. Utilisez l' <xref:System.Transactions.TransactionScope> objet pour participer à une transaction qui est gérée automatiquement pour vous.

 Les projets ne sont pas créés avec une référence à l’assembly System. transactions. vous devez donc ajouter manuellement une référence aux projets qui utilisent des transactions.

> [!NOTE]
> L' <xref:System.Transactions> espace de noms est pris en charge dans Windows 2000 ou version ultérieure.

 Le moyen le plus simple d’implémenter une transaction consiste à instancier un <xref:System.Transactions.TransactionScope> objet dans une `using` instruction. (Pour plus d’informations, consultez [instruction using](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)et [instruction using](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) Le code qui s’exécute dans l' `using` instruction participe à la transaction.

 Pour valider la transaction, appelez la <xref:System.Transactions.TransactionScope.Complete%2A> méthode en tant que dernière instruction dans le bloc using.

 Pour restaurer la transaction, levez une exception avant d’appeler la <xref:System.Transactions.TransactionScope.Complete%2A> méthode.

 Pour plus d’informations, consultez [enregistrer des données dans une transaction](../data-tools/save-data-in-a-transaction.md).

### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>Pour ajouter une référence à la DLL System. transactions

1. Dans le menu **Projet**, sélectionnez **Ajouter une référence**.

2. Sous l’onglet **.net** (onglet**SQL Server** pour les projets SQL Server), sélectionnez **System. transactions**, puis cliquez sur **OK**.

     Une référence à System.Transactions.dll est ajoutée au projet.

### <a name="to-save-data-in-a-transaction"></a>Pour enregistrer des données dans une transaction

- Ajoutez du code pour enregistrer des données dans l’instruction using qui contient la transaction. Le code suivant montre comment créer et instancier un <xref:System.Transactions.TransactionScope> objet dans une instruction using :

     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]

## <a name="see-also"></a>Voir aussi
 [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
