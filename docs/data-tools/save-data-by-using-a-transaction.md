---
title: 'Comment : enregistrer des données à l’aide d’une transaction'
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1c5d8d9f961db7c6560f1dd7a73f2ea62a974bac
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174209"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Comment : enregistrer des données à l’aide d’une transaction
Vous enregistrez des données dans une transaction en utilisant le <xref:System.Transactions> espace de noms. Utilisez le <xref:System.Transactions.TransactionScope> objet de participer à une transaction qui est gérée automatiquement pour vous.

Projets ne sont pas créés avec une référence à la *System.Transactions* assembly, vous devez ajouter manuellement une référence aux projets qui utilisent des transactions.

Le moyen le plus simple d’implémenter une transaction consiste à instancier un <xref:System.Transactions.TransactionScope> de l’objet dans un `using` instruction. (Pour plus d’informations, consultez [à l’aide d’instruction](/dotnet/visual-basic/language-reference/statements/using-statement), et [à l’aide d’instruction](/dotnet/csharp/language-reference/keywords/using-statement).) Le code qui s’exécute dans le `using` instruction participe à la transaction.

Pour valider la transaction, appelez le <xref:System.Transactions.TransactionScope.Complete%2A> bloquer la dernière instruction dans l’à l’aide de la méthode.

Pour restaurer la transaction, lève une exception avant d’appeler le <xref:System.Transactions.TransactionScope.Complete%2A> (méthode).

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Pour ajouter une référence à la System.Transactions.dll.

1.  Sur le **projet** menu, sélectionnez **ajouter une référence**.

2.  Sur le **.NET** onglet (**SQL Server** onglet pour les projets SQL Server), sélectionnez **System.Transactions**, puis sélectionnez **OK**.

     Une référence à *System.Transactions.dll* est ajouté au projet.

## <a name="to-save-data-in-a-transaction"></a>Pour enregistrer les données dans une transaction

-   Ajoutez du code pour enregistrer des données dans à l’aide de l’instruction qui contient la transaction. Le code suivant montre comment créer et instancier un <xref:System.Transactions.TransactionScope> objet dans un à l’aide de déclaration :

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
- [Procédure pas à pas : enregistrer des données dans une transaction](../data-tools/save-data-in-a-transaction.md)