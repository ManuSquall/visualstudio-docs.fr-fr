---
title: Générer des opérateurs IEquatable pour les structs
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour générer des opérateurs égal et IEquatable pour les structs.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 05792636e1094c53869f0235145aec73b26deea9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952978"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Générer des opérateurs IEquatable lors de la génération d’égalités pour les structs

Cette génération de code s’applique à :

- C#

**Ce qui suit :** Vous permet de générer des opérateurs **égal** et **IEquatable** pour les [structs](/dotnet/csharp/language-reference/builtin-types/struct).

Dans les **cas suivants :** Vous disposez d’un struct, nous ajouterons automatiquement les IEquatable, ainsi que les opérateurs égal à et différent de.

**Pourquoi**

- si vous implémentez un type de valeur, vous pouvez substituer la méthode **Equals** afin d’améliorer les performances par rapport à l’implémentation par défaut de la méthode Equals sur ValueType.

- Implémenter l’interface IEquatable implémente une méthode Equals () spécifique au type.

## <a name="how-to"></a>Procédures

1. Placez votre curseur quelque part sur la ligne de votre déclaration de struct.

2. Effectuez ensuite l'une des opérations suivantes :

   - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

   - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.

   - Cliquez sur l’icône ![Tournevis](../media/screwdriver-icon.png) qui apparaît dans la marge de gauche.

   ![Générer IEquatable et égal pour les structs](media/generate-equals-structs.png)

3. Sélectionnez **générer Equals (Object)** dans le menu déroulant.

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)