---
title: Vous avez sélectionné un objet de base de données dans un fournisseur de base de données non pris en charge
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 209ab92e3a24733e2ef4b7b912a36ae920ffffdb
ms.sourcegitcommit: 59c48e1e42b48ad25a4e198af670faa4d8dae370
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54204244"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Vous avez sélectionné un objet de base de données dans un fournisseur de base de données non pris en charge

Le **Concepteur O/R** prend en charge uniquement le fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient>). Bien que vous puissiez cliquer sur **OK** et continuer d’utiliser des objets de fournisseurs de base de données non pris en charge, vous risquez de rencontrer des comportements inattendus au moment de l’exécution.

> [!NOTE]
> Seules les connexions de données qui utilisent le fournisseur de données .NET Framework pour SQL Server sont prises en charge.

## <a name="options"></a>Options

- Cliquez sur **OK** pour continuer de concevoir les classes d'entité qui mappent à la connexion utilisée par le fournisseur de bases de données non pris en charge. Vous risquez de rencontrer des comportements inattendus en utilisant des fournisseurs de base de données non pris en charge.

- Cliquez sur **Annuler** pour arrêter l’action. Créez ou utilisez une connexion de données différente qui utilise le fournisseur .NET Framework pour SQL Server.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)