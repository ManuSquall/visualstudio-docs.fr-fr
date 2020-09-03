---
title: Un ou plusieurs éléments sélectionnés contiennent un type de données qui n’est pas pris en charge par le concepteur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e208b697da1c25dfa2e152ad08096f61c876ebe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658051"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Un ou plusieurs éléments sélectionnés contient un type de données non pris en charge par le concepteur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un ou plusieurs des éléments déplacés à partir de **Explorateur de serveurs** / **Explorateur de base de données** vers le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] contient un type de données qui n’est pas pris en charge par [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (par exemple, les [types CLR définis](https://msdn.microsoft.com/library/9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2)par l’utilisateur).

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Créez une vue basée sur la table souhaitée qui n'inclut pas le type de données non pris en charge.

2. Faites glisser la vue de **Explorateur de serveurs** / **Explorateur de base de données** vers le concepteur.

## <a name="see-also"></a>Voir aussi
 [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [procédure pas à pas : création de classes de LINQ to SQL (Concepteur O-R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
