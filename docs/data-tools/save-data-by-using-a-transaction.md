---
title: Guide pratique pour enregistrer des données avec une transaction
description: Consultez Comment enregistrer des données à l’aide d’une transaction avec les outils de DataSet dans Visual Studio. Vous enregistrez des données dans une transaction à l’aide de l’espace de noms System. transactions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c22a0cc9b0b9d37a4d725aa8ce494646e7779f0f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216070"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Guide pratique pour enregistrer des données avec une transaction

Vous enregistrez des données dans une transaction à l’aide de l' <xref:System.Transactions> espace de noms. Utilisez l' <xref:System.Transactions.TransactionScope> objet pour participer à une transaction qui est gérée automatiquement pour vous.

Les projets ne sont pas créés avec une référence à l’assembly *System. transactions* . vous devez donc ajouter manuellement une référence aux projets qui utilisent des transactions.

Le moyen le plus simple d’implémenter une transaction consiste à instancier un <xref:System.Transactions.TransactionScope> objet dans une `using` instruction. (Pour plus d’informations, consultez [instruction using](/dotnet/visual-basic/language-reference/statements/using-statement)et [instruction using](/dotnet/csharp/language-reference/keywords/using-statement).) Le code qui s’exécute dans l' `using` instruction participe à la transaction.

Pour valider la transaction, appelez la <xref:System.Transactions.TransactionScope.Complete%2A> méthode en tant que dernière instruction dans le bloc using.

Pour restaurer la transaction, levez une exception avant d’appeler la <xref:System.Transactions.TransactionScope.Complete%2A> méthode.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Pour ajouter une référence au System.Transactions.dll

1. Dans le menu **Projet**, sélectionnez **Ajouter une référence**.

2. Sous l’onglet **.net** (onglet **SQL Server** pour les projets SQL Server), sélectionnez **System. transactions**, puis cliquez sur **OK**.

     Une référence à *System.Transactions.dll* est ajoutée au projet.

## <a name="to-save-data-in-a-transaction"></a>Pour enregistrer des données dans une transaction

- Ajoutez du code pour enregistrer des données dans l’instruction using qui contient la transaction. Le code suivant montre comment créer et instancier un <xref:System.Transactions.TransactionScope> objet dans une instruction using :

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet11":::

## <a name="see-also"></a>Voir aussi

- [Enregistrer les données dans la base de données](../data-tools/save-data-back-to-the-database.md)
- [Procédure pas à pas : enregistrer des données dans une transaction](../data-tools/save-data-in-a-transaction.md)
