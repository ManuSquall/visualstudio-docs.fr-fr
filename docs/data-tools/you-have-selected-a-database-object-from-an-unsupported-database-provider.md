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
ms.openlocfilehash: 5b6eef41ebd3ae6fc08029a618cf276e22001235
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37116874"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Vous avez sélectionné un objet de base de données dans un fournisseur de base de données non pris en charge

Le **Concepteur O/R** prend en charge uniquement le fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient>). Bien que vous pouvez cliquer sur **OK** et continuer à travailler avec des objets provenant de fournisseurs de base de données non pris en charge, vous pouvez rencontrer un comportement inattendu au moment de l’exécution.

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
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)