---
title: Générer un champ privé à partir d’un constructeur
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ef4188216b669b30b7af9bd725ec432bcd0a774
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527660"
---
# <a name="generate-private-field-from-constructor"></a>Générer un champ privé à partir d’un constructeur

Cette refactorisation s’applique à : 

- C# 

**Ce qui suit :** Génère un champ privé à partir d’un constructeur. 

Dans les **cas suivants :** Vous souhaitez ajouter rapidement un champ privé à partir d’un constructeur.

**Pourquoi :** L’écriture de champs privés peut être longue et répétitive. L’utilisation de cette refactorisation est rapide et rend le programme plus robuste.

## <a name="how-to"></a>Procédures 

1. Placez le curseur sur le nom du paramètre dans le constructeur.

2. Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.
   
3. Sélectionnez l’option permettant de **créer et d’initialiser le champ**.

   ![Générer un champ privé à partir d’un constructeur](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Voir aussi 

- [Refactorisation](../refactoring-in-visual-studio.md)
