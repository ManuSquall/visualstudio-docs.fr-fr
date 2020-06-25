---
title: Générer des opérateurs de comparaison pour les types qui implémentent IComparable
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 31e33b562a5a11ff77c1d610fbce9e90506b036d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290335"
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

   - Cliquez sur le bouton ![Tournevis](../media/screwdriver-icon.png) qui apparaît dans la marge de gauche.

   ![Générer des opérateurs de comparaison](media/generate-comparison-operators.png)

3. Sélectionnez **générer Equals (Object)** dans le menu déroulant.

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
