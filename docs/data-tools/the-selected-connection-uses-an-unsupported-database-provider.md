---
title: La connexion sélectionnée utilise un fournisseur de base de données non pris en charge
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e6ebdca67dd87f25111ba48c3d9baa346d00e4db
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923809"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connexion sélectionnée utilise un fournisseur de base de données non pris en charge

Ce message apparaît lorsque vous faites glisser des éléments qui n’utilisent pas le fournisseur de données .NET Framework pour SQL Server à partir de **Explorateur de serveurs** ou **Database Explorer** sur la [des outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

Le **Concepteur O/R** prend en charge uniquement les connexions de données qui utilisent le fournisseur .NET Framework pour SQL Server. Seules les connexions à Microsoft SQL Server ou aux fichiers de base de données Microsoft SQL Server sont valides.

Pour corriger cette erreur, ajoutez uniquement des éléments à partir de connexions de données qui utilisent le fournisseur de données .NET Framework pour SQL Server pour le **Concepteur O/R**.

## <a name="see-also"></a>Voir aussi

- <xref:System.Data.SqlClient>
- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
