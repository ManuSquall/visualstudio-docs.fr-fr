---
title: Générer la refactorisation des paramètres
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
ms.openlocfilehash: 372a3f705e5e85c0edb31a754105f61056402b9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094341"
---
# <a name="generate-parameter"></a>Générer un paramètre

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Ce qui suit :** Génère automatiquement un paramètre de méthode.

Dans les **cas suivants :** Vous faites référence à une variable dans une méthode qui n’existe pas dans le contexte actuel et qui reçoit une erreur. vous pouvez générer un paramètre en tant que correctif de code. 

**Pourquoi :** Vous pouvez modifier rapidement une signature de méthode sans perdre de contexte.

## <a name="how-to"></a>Procédures

1. Placez le curseur dans le nom de la variable et appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
1. Sélectionnez **Générer un paramètre**.

   ![Générer un paramètre](media/generate-parameter.png) 

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
