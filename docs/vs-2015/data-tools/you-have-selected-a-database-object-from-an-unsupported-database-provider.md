---
title: Vous avez sélectionné un objet de base de données à partir d’un fournisseur de base de données non pris en charge | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8e051a5533f02946e9e28a08abd4c4a1326aca8f
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879301"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Vous avez sélectionné un objet de base de données dans un fournisseur de base de données non pris en charge
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Documentation Visual Studio 2017](/visualstudio/).  
  
Le [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) prend en charge uniquement le fournisseur de données .NET Framework pour SQL Server (<xref:System.Data.SqlClient>). Bien que vous pouvez cliquer sur **OK** et continuer à travailler avec des objets provenant de fournisseurs de base de données non pris en charge, vous pouvez rencontrer un comportement inattendu au moment de l’exécution.  
  
> [!NOTE]
>  Seules les connexions de données qui utilisent le fournisseur de données .NET Framework pour SQL Server sont prises en charge.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Cliquez sur **OK** pour continuer de concevoir les classes d’entité qui mappent à la connexion qui utilise le fournisseur de base de données non pris en charge. Vous risquez de rencontrer des comportements inattendus en utilisant des fournisseurs de base de données non pris en charge.  
  
     - ou -  
  
-   Cliquez sur **Annuler**.  
  
     L'action est arrêtée. Créez ou utilisez une connexion de données qui utilise le fournisseur .NET Framework pour SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Fournisseurs de données .NET framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Connexion aux données dans Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)

