---
title: Vous avez sélectionné un objet de base de données à partir d’un fournisseur de base de données non pris en charge | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b8ecec386030299be7b6c9571218dec0c3396440
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073590"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Vous avez sélectionné un objet de base de données dans un fournisseur de base de données non pris en charge
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) prend en charge uniquement le fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient>). Bien que vous puissiez cliquer sur **OK** et continuer d’utiliser des objets de fournisseurs de base de données non pris en charge, vous risquez de rencontrer des comportements inattendus au moment de l’exécution.  
  
> [!NOTE]
>  Seules les connexions de données qui utilisent le fournisseur de données .NET Framework pour SQL Server sont prises en charge.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Cliquez sur **OK** pour continuer de concevoir les classes d'entité qui mappent à la connexion utilisée par le fournisseur de bases de données non pris en charge. Vous risquez de rencontrer des comportements inattendus en utilisant des fournisseurs de base de données non pris en charge.  
  
     - ou -  
  
- Cliquez sur **Annuler**.  
  
     L'action est arrêtée. Créez ou utilisez une connexion de données qui utilise le fournisseur .NET Framework pour SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Fournisseurs de données .NET Framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   