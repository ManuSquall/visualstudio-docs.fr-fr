---
title: La propriété ne peut pas être supprimée, car il participe à l’association
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9e65049ae881ff11cd647fe09df3a6919dd8818c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>La propriété &lt;nom de la propriété&gt; ne peut pas être supprimé, car il participe à l’association &lt;nom de l’association&gt;

La propriété sélectionnée est définie comme la **propriété d’Association** pour l’association entre les classes indiquée dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à une association entre des classes de données.

Définir le **propriété d’Association** à une autre propriété de la classe de données pour permettre la suppression de la propriété désirée.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Dans le Concepteur O/R, sélectionnez la ligne d'association qui connecte les classes de données indiquées dans le message d'erreur.

2. Double-cliquez sur la ligne pour ouvrir la **Éditeur d’associations** boîte de dialogue.

3. Supprimez la propriété à partir de la **propriétés d’Association**.

4. Essayez une nouvelle fois de supprimer la propriété.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL des outils dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)