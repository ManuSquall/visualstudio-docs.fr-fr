---
title: Générer la refactorisation des paramètres
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e95e76c35afdb8cdbe38c8b33329734ba68361b1
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329038"
---
# <a name="generate-parameter"></a>Générer un paramètre

Cette refactorisation s’applique à :

- C#

**Quoi :** Génère automatiquement un paramètre de méthode.

**Quand :** Vous référencez une variable dans une méthode qui n’existe pas dans le contexte actuel et recevez une erreur ; vous pouvez générer un paramètre comme correctif de code. 

**Pourquoi :** Vous pouvez rapidement modifier une signature de méthode sans perdre le contexte.

## <a name="how-to"></a>Procédure

1. Placez votre curseur sur le nom de la variable, puis appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.
1. Sélectionnez **Générer un paramètre**.

   ![Générer un paramètre](media/generate-parameter.png) 

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
