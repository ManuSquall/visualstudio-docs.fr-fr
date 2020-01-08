---
title: Guide pratique pour enregistrer des données avec une transaction
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: beadb43d7eed78f04fc60ce1307045e9badac205
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586274"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Guide pratique pour enregistrer des données avec une transaction

Vous enregistrez des données dans une transaction à l’aide de l’espace de noms <xref:System.Transactions>. Utilisez l’objet <xref:System.Transactions.TransactionScope> pour participer à une transaction qui est gérée automatiquement pour vous.

Les projets ne sont pas créés avec une référence à l’assembly *System. transactions* . vous devez donc ajouter manuellement une référence aux projets qui utilisent des transactions.

Le moyen le plus simple d’implémenter une transaction consiste à instancier un objet <xref:System.Transactions.TransactionScope> dans une instruction `using`. (Pour plus d’informations, consultez [instruction using](/dotnet/visual-basic/language-reference/statements/using-statement)et [instruction using](/dotnet/csharp/language-reference/keywords/using-statement).) Le code qui s’exécute dans l’instruction `using` participe à la transaction.

Pour valider la transaction, appelez la méthode <xref:System.Transactions.TransactionScope.Complete%2A> en tant que dernière instruction dans le bloc using.

Pour restaurer la transaction, levez une exception avant d’appeler la méthode <xref:System.Transactions.TransactionScope.Complete%2A>.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Pour ajouter une référence à System. transactions. dll

1. Dans le menu **Projet**, sélectionnez **Ajouter une référence**.

2. Sous l’onglet **.net** (onglet**SQL Server** pour les projets SQL Server), sélectionnez **System. transactions**, puis cliquez sur **OK**.

     Une référence à *System. transactions. dll* est ajoutée au projet.

## <a name="to-save-data-in-a-transaction"></a>Pour enregistrer des données dans une transaction

- Ajoutez du code pour enregistrer des données dans l’instruction using qui contient la transaction. Le code suivant montre comment créer et instancier un objet <xref:System.Transactions.TransactionScope> dans une instruction using :

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
- [Procédure pas à pas : enregistrer des données dans une transaction](../data-tools/save-data-in-a-transaction.md)
