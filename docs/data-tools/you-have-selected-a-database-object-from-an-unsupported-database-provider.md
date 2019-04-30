---
title: Vous avez sélectionné un objet de base de données dans un fournisseur de base de données non pris en charge
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 13e6dd42ed372fb28d850a566ea1900447ad220c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564676"
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