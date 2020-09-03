---
title: Vous avez sélectionné un objet de base de données à partir d’un fournisseur de base de données non pris en charge | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 05a4407eba52ec3940b70ffab220ef354af90e9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657790"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Vous avez sélectionné un objet de base de données dans un fournisseur de base de données non pris en charge
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ) prend uniquement en charge les .NET Framework Fournisseur de données pour SQL Server ( <xref:System.Data.SqlClient> ). Bien que vous puissiez cliquer sur **OK** et continuer d’utiliser des objets de fournisseurs de base de données non pris en charge, vous risquez de rencontrer des comportements inattendus au moment de l’exécution.

> [!NOTE]
> Seules les connexions de données qui utilisent le fournisseur de données .NET Framework pour SQL Server sont prises en charge.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Cliquez sur **OK** pour continuer de concevoir les classes d'entité qui mappent à la connexion utilisée par le fournisseur de bases de données non pris en charge. Vous risquez de rencontrer des comportements inattendus en utilisant des fournisseurs de base de données non pris en charge.

     - ou -

- Cliquez sur **Annuler**.

     L'action est arrêtée. Créez ou utilisez une connexion de données qui utilise le fournisseur .NET Framework pour SQL Server.

## <a name="see-also"></a>Voir aussi
 [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [.NET Framework fournisseurs de données](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)