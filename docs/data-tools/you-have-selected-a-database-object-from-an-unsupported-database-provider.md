---
title: Vous avez sélectionné un objet de base de données dans un fournisseur de base de données non pris en charge
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f3ab7375db8c3adfe769cf1c344937b60695eb25
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Vous avez sélectionné un objet de base de données dans un fournisseur de base de données non pris en charge

Le Concepteur O/R prend en charge uniquement le fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient>). Bien que vous pouvez cliquer sur **OK** et continuer à travailler avec des objets provenant de fournisseurs de base de données non pris en charge, vous pouvez rencontrer un comportement inattendu au moment de l’exécution.

> [!NOTE]
> Seules les connexions de données qui utilisent le fournisseur de données .NET Framework pour SQL Server sont prises en charge.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Cliquez sur **OK**.

   Vous pouvez continuer à concevoir les classes d’entité qui mappent à la connexion qui utilise le fournisseur de base de données non pris en charge. Vous risquez de rencontrer des comportements inattendus en utilisant des fournisseurs de base de données non pris en charge.

    - ou -

- Cliquez sur **Annuler**.

   L'action est arrêtée. Créez ou utilisez une connexion de données qui utilise le fournisseur .NET Framework pour SQL Server.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)