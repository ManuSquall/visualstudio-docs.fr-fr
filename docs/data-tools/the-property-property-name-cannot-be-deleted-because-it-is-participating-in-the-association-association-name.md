---
title: La propriété ne peut pas être supprimée, car il participe à l’association
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6ed6b14f64d16d1f18d4b358761169c3d424cee8
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174060"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>La propriété &lt;nom de la propriété&gt; ne peut pas être supprimé, car il participe à l’association &lt;nom de l’association&gt;

La propriété sélectionnée est définie comme le **propriété d’Association** pour l’association entre les classes indiquées dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à une association entre des classes de données.

Définir le **propriété d’Association** à une autre propriété de la classe de données pour permettre la suppression de la propriété désirée.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Sélectionnez la ligne d’association sur le **Concepteur O/R** qui connecte les classes de données indiquées dans le message d’erreur.

2. Double-cliquez sur la ligne pour ouvrir la **Éditeur d’associations** boîte de dialogue.

3. Supprimez la propriété à partir de la **propriétés d’Association**.

4. Essayez une nouvelle fois de supprimer la propriété.

## <a name="see-also"></a>Voir aussi

- [Messages du Concepteur O/R](../data-tools/o-r-designer-messages.md)
- [Outils LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)