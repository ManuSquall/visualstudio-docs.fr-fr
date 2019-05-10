---
title: Impossible de supprimer la propriété, car elle participe à l’association
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d277919229316768cde27efdc9b2797d0351e9fe
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458504"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Impossible de supprimer la propriété &lt;nom de la propriété&gt;, car elle participe à l’association &lt;nom de l’association&gt;

La propriété sélectionnée est définie comme **Propriété d’association** pour l’association de classes indiquée dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à une association entre des classes de données.

Affectez à **Propriété d’association** une propriété différente de la classe de données pour permettre la suppression de la propriété voulue.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Dans le **Concepteur O/R**, sélectionnez la ligne d’association qui connecte les classes de données indiquées dans le message d’erreur.

2. Double-cliquez sur la ligne pour ouvrir la boîte de dialogue **Éditeur d’associations**.

3. Supprimez la propriété des **Propriétés d’association**.

4. Essayez une nouvelle fois de supprimer la propriété.

## <a name="see-also"></a>Voir aussi

- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)