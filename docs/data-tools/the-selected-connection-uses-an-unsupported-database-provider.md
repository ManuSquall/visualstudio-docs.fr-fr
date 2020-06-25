---
title: La connexion sélectionnée utilise un fournisseur de base de données non pris en charge
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 52b88e1de91c2b2da629b6b9034ac552b8d88d5d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281316"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connexion sélectionnée utilise un fournisseur de base de données non pris en charge

Ce message s’affiche lorsque vous faites glisser des éléments qui n’utilisent pas la .NET Framework Fournisseur de données pour SQL Server à partir de **Explorateur de serveurs** ou **Explorateur de base de données** sur les [outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

Le **Concepteur O/R** prend en charge uniquement les connexions de données qui utilisent le fournisseur de .NET Framework pour SQL Server. Seules les connexions à Microsoft SQL Server ou aux fichiers de base de données Microsoft SQL Server sont valides.

Pour corriger cette erreur, ajoutez uniquement les éléments des connexions de données qui utilisent le Fournisseur de données .NET Framework pour SQL Server au **Concepteur O/R**.

## <a name="see-also"></a>Voir aussi

- <xref:System.Data.SqlClient>
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
