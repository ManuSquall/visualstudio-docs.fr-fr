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
ms.openlocfilehash: 6563cc81be8f026a9b2230b0664c678b5649ca9e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907475"
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

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)