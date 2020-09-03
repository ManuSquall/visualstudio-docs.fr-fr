---
title: Conversion de type anonyme en classe
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2379ce588eeb4773e562f630ade37e28d7f17315
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094295"
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
