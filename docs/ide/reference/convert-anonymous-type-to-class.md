---
title: Conversion de type anonyme en classe
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour convertir un type anonyme en classe dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
monikerRange: '>= vs-2019'
ms.openlocfilehash: 19e755e4b56675265d85a416684f2b42bd7ccd13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907657"
---
# <a name="convert-anonymous-type-to-class"></a>Conversion de type anonyme en classe

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Ce qui suit :** Convertit un type anonyme en classe.

Dans les **cas suivants :** Vous avez un type anonyme que vous souhaitez continuer à créer dans une classe.

**Pourquoi :** Les types anonymes sont utiles si vous les utilisez uniquement localement. À mesure que votre code se développe, il est intéressant de disposer d’un moyen simple de le promouvoir en classe.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans un type anonyme.
2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Conversion de type anonyme en classe](media/convert-anon-to-class.png)

2. Appuyez sur **Entrée** pour accepter la refactorisation.

   ![Conversion de type anonyme en classe acceptée](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
