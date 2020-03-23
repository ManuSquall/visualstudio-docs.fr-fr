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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094341"
---
# <a name="generate-parameter"></a>Générer un paramètre

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Génère automatiquement un paramètre de méthode.

**Quand :** Vous faites référence à une variable dans une méthode qui n’existe pas dans le contexte actuel et recevez une erreur; vous pouvez générer un paramètre comme un correctif de code. 

**Pourquoi:** Vous pouvez rapidement modifier une signature de méthode sans perdre de contexte.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans le nom variable et appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
1. Sélectionnez **Générer un paramètre**.

   ![Générer un paramètre](media/generate-parameter.png) 

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
