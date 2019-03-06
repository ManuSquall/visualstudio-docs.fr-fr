---
title: Un ou plusieurs éléments sélectionnés contient un type de données non pris en charge par le concepteur
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 12ec2ed7dc2a12556fcb6eeeddbe2d0745ae7f72
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55928516"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Un ou plusieurs éléments sélectionnés contient un type de données non pris en charge par le concepteur

Un ou plusieurs des éléments déplacés à partir de **Explorateur de serveurs** ou **Database Explorer** sur le **Concepteur O/R** contient un type de données qui n’est pas pris en charge par le **O /R concepteur**, par exemple, [types CLR définis par l’utilisateur](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Créez une vue basée sur la table souhaitée qui n'inclut pas le type de données non pris en charge.

2. Faites glisser la vue à partir de **Explorateur de serveurs** ou **Database Explorer** sur le concepteur.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)