---
title: Refactoriser - Renommer
ms.date: 01/26/2018
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
ms.openlocfilehash: 4dbccd4732f56d671fd74f59916885ea338136f8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565459"
---
# <a name="rename-a-code-symbol-refactoring"></a>Renommer un symbole de code (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de renommer des identificateurs pour des symboles de code, tels que des champs, variables locales, méthodes, espaces de noms, propriétés et types.

**Quand :** vous voulez renommer en toute sécurité un élément sans avoir à rechercher toutes les instances et à copier/coller le nouveau nom.

**Pourquoi :** un copier-coller du nouveau nom dans un projet entier entraînera probablement des erreurs. Cet outil de refactorisation effectuera avec précision le changement de nom.

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

## <a name="remarks"></a>Notes

- À compter de Visual Studio 2019 version 16,3, lorsque vous renommez un type qui correspond au nom du fichier dans lequel il se trouve, une case à cocher s’affiche pour vous permettre de renommer le fichier en même temps. Cette option apparaît lorsque vous renommez une classe, une interface ou une énumération. Cette option n’est pas prise en charge pour les types partiels avec plusieurs définitions.

   ![Renommer l’animation avec le fichier-C#](media/rename-with-file-animated-cs.gif)

- Si vous utilisez un nom qui existe déjà, ce qui provoquerait un conflit, la boîte de dialogue **Renommer** vous avertit.

   ![Conflit de changement de nom](media/rename-conflict-cs.png)

- Une autre façon de renommer un symbole consiste à modifier son nom dans l’éditeur. Ensuite, placez le curseur dans le nom du symbole et appuyez sur **Ctrl**+ **.** ou développez simplement le menu de l’icône Ampoule qui s’affiche et choisissez **Renommer \<ancien nom> par \<nouveau nom>** .

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
