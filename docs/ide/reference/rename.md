---
title: Refactoriser - Renommer
ms.date: 05/04/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8d5b3d32b23b336dc86a92c33bcb97d02312f2dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84182953"
---
# <a name="rename-a-code-symbol-refactoring"></a>Renommer un symbole de code (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de renommer des identificateurs pour des symboles de code, tels que des champs, variables locales, méthodes, espaces de noms, propriétés et types.

**Quand :** vous voulez renommer en toute sécurité un élément sans avoir à rechercher toutes les instances et à copier/coller le nouveau nom.

**Pourquoi :** un copier-coller du nouveau nom dans un projet entier entraînera probablement des erreurs. Cet outil de refactorisation effectuera avec précision le changement de nom.

## <a name="how-to"></a>Procédures

1. Mettez en surbrillance ou placez le curseur de texte dans l’élément à renommer :

   - C# :

       ![Code mis en surbrillance (C#)](media/rename-highlight-cs.png)

   - Visual Basic :

       ![Code mis en surbrillance (Visual Basic)](media/rename-highlight-vb.png)

2. Ensuite, utilisez le clavier ou la souris comme suit :

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

## <a name="remarks"></a>Notes

- À compter de Visual Studio 2019 version 16,3, lorsque vous renommez un type qui correspond au nom du fichier dans lequel il se trouve, une case à cocher s’affiche pour vous permettre de renommer le fichier en même temps. Cette option apparaît lorsque vous renommez une classe, une interface ou une énumération. Cette option n’est pas prise en charge pour les types partiels avec plusieurs définitions.

   ![Renommer l’animation avec le fichier-C #](media/rename-with-file-animated-cs.gif)

- Si vous utilisez un nom qui existe déjà, ce qui provoquerait un conflit, la boîte de dialogue **Renommer** vous avertit.

   ![Conflit de changement de nom](media/rename-conflict-cs.png)

- Une autre façon de renommer un symbole consiste à modifier son nom dans l’éditeur. Ensuite, avec le curseur dans le nom du symbole, appuyez sur **CTRL** + **.** vous pouvez aussi développer le menu représentant une icône d’ampoule qui s’affiche et choisir **Renommer \<old name> en \<new name> **.

   ![Renommer dans l’éditeur](media/rename-with-editor-cs.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
