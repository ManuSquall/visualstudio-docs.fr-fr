---
title: Extraire une interface (refactorisation)
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour créer une interface à l’aide de membres existants à partir d’une classe, d’une structure ou d’une interface.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 12db627bde45d11950e661d258c9891b8e935ba1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861034"
---
# <a name="extract-an-interface-refactoring"></a>Extraire une interface (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Ce qui suit :** Vous permet de créer une interface à l’aide de membres existants à partir d’une classe, d’une structure ou d’une interface.

Dans les **cas suivants :** Vous avez des membres dans une classe, un struct ou une interface qui peuvent être hérités par d’autres classes, structures ou interfaces.

**Pourquoi :** les interfaces sont d’excellentes constructions pour les conceptions orientées objet. Imaginez des classes représentant différents animaux (chien, chat, oiseau) pouvant être associées à des méthodes courantes, par exemple Manger, Boire et Dormir. Une interface comme IAnimal permettrait aux éléments Chien, Chat et Oiseai d’avoir la même « signature » pour ces méthodes.

## <a name="extract-an-interface-refactoring"></a>Extraire une interface (refactorisation)

1. Placez votre curseur dans le nom de la classe.

   - C# :

       ![Code mis en surbrillance (C#)](media/extractinterface-highlight-cs.png)

   - Visual Basic :

       ![Code mis en surbrillance (Visual Basic)](media/extractinterface-highlight-vb.png)

2. Effectuez ensuite l’une des actions suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl+R**, puis **Ctrl+I**. (Le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
      - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire l’interface** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
      - Sélectionnez **Modifier > Refactoriser > Extraire l’interface**.
      - Cliquez avec le bouton droit sur le nom de la classe et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire l’interface** dans la fenêtre contextuelle d’aperçu.

3. Dans la boîte de dialogue **Extraire l’interface** qui s’affiche, entrez les informations demandées :

   ![Extraire l'interface](media/extractinterface-dialog-same-file.png)

   | Champ | Description |
   | - | - |
   | **Nouveau nom d’interface** | Nom de l'interface à créer. Ce nom a par défaut la valeur I *ClassName*, où *ClassName* correspond au nom de la classe que vous avez sélectionné ci-dessus. |
   | **Nouveau nom de fichier** | Nom du fichier généré qui contiendra l’interface. Comme pour le nom de l’interface, ce nom a par défaut la valeur I *ClassName*, où *ClassName* correspond au nom de la classe que vous avez sélectionné ci-dessus. Vous pouvez également sélectionner l’option **Ajouter au fichier actuel**. |
   | **Sélectionner les membres publics pour former l'interface** | Les éléments à extraire dans l’interface. Vous pouvez sélectionner autant d’éléments que vous le souhaitez. |

4. Choisissez **OK**.

   L’interface est créée dans le fichier portant le nom spécifié. De plus, la classe que vous avez sélectionnée implémente cette interface.

   - C# :

      ![Classe résultante - C#](media/extractinterface-class-cs.png)

      ![Interface résultante - C#](media/extractinterface-interface-cs.png)

   - Visual Basic :

      ![Classe résultante - Visual Basic](media/extractinterface-class-vb.png)

      ![Interface résultante - Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)
