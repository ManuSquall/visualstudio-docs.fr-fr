---
title: Refactoriser - Renommer
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a24c8a44cbd7d3c889d92c34c9eac0c5b015be65
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53881008"
---
# <a name="rename-a-code-symbol-refactoring"></a>Renommer un symbole de code (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Vous permet de renommer des identificateurs pour des symboles de code, tels que des champs, variables locales, méthodes, espaces de noms, propriétés et types.

**Quand :** Vous voulez renommer en toute sécurité un élément sans avoir à rechercher toutes les instances et à copier/coller le nouveau nom.

**Pourquoi :** Un copier-coller du nouveau nom dans un projet entier entraînera probablement des erreurs. Cet outil de refactorisation effectuera avec précision le changement de nom.

## <a name="how-to"></a>Procédure

1. Mettez en surbrillance ou placez le curseur de texte dans l’élément à renommer :

   - C# :

       ![Code mis en surbrillance (C#)](media/rename-highlight-cs.png)

   - Visual Basic :

       ![Code mis en surbrillance (Visual Basic)](media/rename-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl+R**, puis **Ctrl+R**. (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
   - **Souris**
      - Sélectionnez **Modifier > Refactoriser > Renommer**.
      - Cliquez avec le bouton droit et sélectionnez **Renommer**.

3. Renommez l’élément en tapant le nouveau nom.

   - C# :

      ![Renommer une animation (C#)](media/rename-animated-cs.gif)

   - Visual Basic :

      ![Renommer (VB)](media/rename-rename-vb.png)

   > [!TIP]
   > Vous pouvez aussi mettre à jour les commentaires et d’autres chaînes pour utiliser ce nouveau nom, et [afficher un aperçu des changements](../../ide/preview-changes.md) avant de les enregistrer, en utilisant les cases à cocher de la boîte de dialogue **Renommer** qui apparaît en haut à droite de votre éditeur.

4. Quand vous êtes satisfait du changement, appuyez sur le bouton **Appliquer** ou sur la touche **Entrée** pour valider les changements.

> [!NOTE]
> Si vous utilisez un nom qui existe déjà, ce qui provoquerait un conflit, la boîte de dialogue **Renommer** vous avertit.
>
> ![Conflit de changement de nom](media/rename-conflict-cs.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
