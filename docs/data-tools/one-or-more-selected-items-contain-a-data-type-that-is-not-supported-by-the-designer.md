---
title: Un ou plusieurs éléments sélectionnés contient un type de données non pris en charge par le concepteur
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 294bc51345eb6a9e09f9892c3b9ec17f78c42451
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986122"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Un ou plusieurs éléments sélectionnés contient un type de données non pris en charge par le concepteur

Un ou plusieurs des éléments déplacés à partir de **Explorateur de serveurs** ou **Database Explorer** sur le **Concepteur O/R** contient un type de données qui n’est pas pris en charge par le **O /R concepteur**, par exemple, [types CLR définis par l’utilisateur](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Créez une vue basée sur la table souhaitée qui n'inclut pas le type de données non pris en charge.

2. Faites glisser la vue à partir de **Explorateur de serveurs** ou **Database Explorer** sur le concepteur.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)