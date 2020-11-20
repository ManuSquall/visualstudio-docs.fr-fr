---
title: La propriété participe à l’Association
description: La propriété ne peut pas être supprimée, car elle participe à l’Association. Affichez des informations sur ce message d’Concepteur Objet Relationnel (Concepteur O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a0d39fa3d7740996be3fc9da75224739f1e55539
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998371"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Impossible de supprimer la propriété &lt;nom de la propriété&gt;, car elle participe à l’association &lt;nom de l’association&gt;

La propriété sélectionnée est définie comme **Propriété d’association** pour l’association de classes indiquée dans le message d’erreur. Les propriétés ne peuvent pas être supprimées si elles participent à une association entre des classes de données.

Affectez à **Propriété d’association** une propriété différente de la classe de données pour permettre la suppression de la propriété voulue.

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Dans le **Concepteur O/R** , sélectionnez la ligne d’association qui connecte les classes de données indiquées dans le message d’erreur.

2. Double-cliquez sur la ligne pour ouvrir la boîte de dialogue **Éditeur d’associations**.

3. Supprimez la propriété des **Propriétés d’association**.

4. Essayez une nouvelle fois de supprimer la propriété.

## <a name="see-also"></a>Voir aussi

- [Outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)