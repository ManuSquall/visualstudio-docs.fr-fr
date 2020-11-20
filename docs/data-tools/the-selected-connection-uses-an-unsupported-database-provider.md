---
title: Fournisseur de base de données non pris en charge
description: La connexion sélectionnée utilise un fournisseur de base de données non pris en charge. Affichez des informations sur ce message de Concepteur Objet Relationnel Visual Studio (Concepteur O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 06e08f9a9c28698ae2ee2fecfbcec64c39666c8a
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998345"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connexion sélectionnée utilise un fournisseur de base de données non pris en charge

Ce message s’affiche lorsque vous faites glisser des éléments qui n’utilisent pas la .NET Framework Fournisseur de données pour SQL Server à partir de **Explorateur de serveurs** ou **Explorateur de base de données** sur les [outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

Le **Concepteur O/R** prend en charge uniquement les connexions de données qui utilisent le fournisseur de .NET Framework pour SQL Server. Seules les connexions à Microsoft SQL Server ou aux fichiers de base de données Microsoft SQL Server sont valides.

Pour corriger cette erreur, ajoutez uniquement les éléments des connexions de données qui utilisent le Fournisseur de données .NET Framework pour SQL Server au **Concepteur O/R**.

## <a name="see-also"></a>Voir aussi

- <xref:System.Data.SqlClient>
- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
