---
title: Un ou plusieurs éléments sélectionnés contiennent un type de données qui n’est pas pris en charge par le Concepteur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 966adc7a4114c54479c0ad8c52a604e0fb5d3380
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Un ou plusieurs éléments sélectionnés contient un type de données non pris en charge par le concepteur
Un ou plusieurs des éléments déplacés à partir de **l’Explorateur de serveurs**/**l’Explorateur de base de données** sur la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] contient un type de données qui n’est pas pris en charge par le [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] par exemple, [Types CLR définis par l’utilisateur](/dotnet/framework/data/adonet/sql/clr-user-defined-types).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Créez une vue basée sur la table souhaitée qui n'inclut pas le type de données non pris en charge.  
  
2.  Faites glisser la vue à partir de **l’Explorateur de serveurs**/**l’Explorateur de base de données** sur le concepteur.  
  
## <a name="see-also"></a>Voir aussi
[Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)