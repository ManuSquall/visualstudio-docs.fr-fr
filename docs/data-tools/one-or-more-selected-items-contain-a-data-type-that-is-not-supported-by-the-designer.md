---
title: Un ou plusieurs éléments sélectionnés contient un type de données non pris en charge par le concepteur
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d2f066bb7501085b66ba724f94840314063cd2ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281888"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Un ou plusieurs éléments sélectionnés contient un type de données non pris en charge par le concepteur

Un ou plusieurs des éléments déplacés depuis **Explorateur de serveurs** ou **Explorateur de base de données** vers le **Concepteur o/r** contient un type de données qui n’est pas pris en charge par le **Concepteur o/r**, par exemple, les [types CLR définis](/dotnet/framework/data/adonet/sql/clr-user-defined-types)par l’utilisateur.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Créez une vue basée sur la table souhaitée qui n'inclut pas le type de données non pris en charge.

2. Faites glisser la vue à partir de **Explorateur de serveurs** ou **Explorateur de base de données** dans le concepteur.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
