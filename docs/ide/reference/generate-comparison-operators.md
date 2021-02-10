---
title: Générer des opérateurs de comparaison pour IComparable
ms.custom: SEO-VS-2020
description: Pour des performances accrues, générez des opérateurs de comparaison pour les types qui implémentent IComparable.
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ee0ac916bcc13e6bc89485171b2ce145b31dd919
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932564"
---
# <a name="generate-comparison-operators-for-types-that-implement-icomparable"></a>Générer des opérateurs de comparaison pour les types qui implémentent IComparable

Cette génération de code s’applique à :

- C#

**Ce qui suit :** Vous permet de générer des opérateurs de **comparaison** pour les types qui implémentent IComparable.

Dans les **cas suivants :** Vous disposez d’un type qui implémente IComparable, nous ajouterons automatiquement les opérateurs de comparaison.

**Pourquoi :** Si vous implémentez un type valeur, vous devez envisager de substituer la méthode **Equals** pour améliorer les performances par rapport à l’implémentation par défaut de la méthode Equals sur ValueType.

## <a name="how-to"></a>Procédures

1. Placez votre curseur à l’intérieur de la classe ou sur le mot clé IComparable.

2. Effectuez ensuite l'une des opérations suivantes :

   - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

   - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.

   - Cliquez sur l’icône ![Tournevis](../media/screwdriver-icon.png) qui apparaît dans la marge de gauche.

   ![Générer des opérateurs de comparaison](media/generate-comparison-operators.png)

3. Sélectionnez **générer Equals (Object)** dans le menu déroulant.

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
