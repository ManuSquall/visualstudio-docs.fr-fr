---
title: Générer un champ privé à partir d’un constructeur
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
ms.openlocfilehash: 4eb5dd39d0fb2d4cd9ba8ade0d0408d6e36a4854
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094017"
---
# <a name="generate-private-field-from-constructor"></a>Générer un champ privé à partir d’un constructeur

Cette refactorisation s’applique à : 

- C# 

- Visual Basic

**Quoi :** Générer un champ privé à partir d’un constructeur. 

**Quand :** Vous souhaitez rapidement ajouter un champ privé à partir d’un constructeur.

**Pourquoi:** Écrire des champs privés peut prendre beaucoup de temps et répétitif. L’utilisation de cette refactorisation est rapide et rend le programme plus robuste.

## <a name="how-to"></a>Procédures 

1. Placez votre curseur sur le nom du paramètre dans le constructeur.

2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
   
3. Sélectionnez l’option pour **créer et initialiser le champ**.

   ![Générer un champ privé à partir d’un constructeur](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Voir aussi 

- [Refactorisation](../refactoring-in-visual-studio.md)
