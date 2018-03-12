---
title: "Vous avez sélectionné un objet de base de données à partir d’un fournisseur de base de données non pris en charge | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 85a8e5883a8d78297336016ac295f9b5d76ce337
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Vous avez sélectionné un objet de base de données dans un fournisseur de base de données non pris en charge
Le Concepteur O/R prend en charge uniquement le fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient>). Bien que vous pouvez cliquer sur **OK** et continuer à travailler avec des objets provenant de fournisseurs de base de données non pris en charge, vous pouvez rencontrer un comportement inattendu au moment de l’exécution.  
  
> [!NOTE]
>  Seules les connexions de données qui utilisent le fournisseur de données .NET Framework pour SQL Server sont prises en charge.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Cliquez sur **OK**.

   Vous pouvez continuer à concevoir les classes d’entité qui mappent à la connexion qui utilise le fournisseur de base de données non pris en charge. Vous risquez de rencontrer des comportements inattendus en utilisant des fournisseurs de base de données non pris en charge.  
  
     - ou -  
  
- Cliquez sur **Annuler**.

   L'action est arrêtée. Créez ou utilisez une connexion de données qui utilise le fournisseur .NET Framework pour SQL Server.  
  
## <a name="see-also"></a>Voir aussi
[Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)