---
title: Extraire une interface (refactorisation) dans Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6afc2acab36be88b4eb554d1900e6b314e395bd9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31948169"
---
# <a name="extract-an-interface-refactoring"></a>Extraire une interface (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de créer une interface en utilisant les membres existants d’une classe, structure ou interface.

**Quand :** vous disposez de plusieurs classes, structures ou interfaces avec des méthodes qui peuvent être mises à la disposition et utilisées par d’autres classes, structures ou interfaces.

**Pourquoi :** les interfaces sont d’excellentes constructions pour les conceptions orientées objet. Imaginez des classes représentant différents animaux (chien, chat, oiseau) pouvant être associées à des méthodes courantes, par exemple Manger, Boire et Dormir. Une interface comme IAnimal permettrait aux éléments Chien, Chat et Oiseai d’avoir la même « signature » pour ces méthodes.

## <a name="how-to"></a>Procédure

1. Mettez en surbrillance le nom de la classe sur laquelle exécuter l’action, ou placez le curseur quelque part dans le nom de classe.

   - C# :

    ![Code mis en surbrillance (C#)](media/extractinterface-highlight-cs.png)

   - Visual Basic :

    ![Code mis en surbrillance (Visual Basic)](media/extractinterface-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
     - Appuyez sur **Ctrl+R**, puis **Ctrl+I**. (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire l’interface** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
     - Sélectionnez **Modifier > Refactoriser > Extraire l’interface**.
     - Cliquez avec le bouton droit sur le nom de la classe et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire l’interface** dans la fenêtre contextuelle d’aperçu.

1. Dans la boîte de dialogue **Extraire l’interface** qui s’affiche, entrez les informations demandées :

   ![Extraire l'interface](media/extractinterface-dialog-cs.png)

   | Champ | Description |
   | --- | --- |
   | **Nouveau nom d’interface** | Nom de l'interface à créer. Cette valeur est définie par défaut sur I*ClassName*, où *ClassName* représente le nom de la classe que vous avez sélectionné ci-dessus. |
   | **Nouveau nom de fichier** | Le nom du fichier qui sera généré et qui contiendra l’interface. Comme pour le nom de l’interface, cette valeur est définie par défaut sur I*ClassName*, où *ClassName* représente le nom de la classe que vous avez sélectionné ci-dessus. |
   | **Sélectionner les membres publics pour former l'interface** | Les éléments à extraire dans l’interface. Vous pouvez sélectionner autant d’éléments que vous le souhaitez. |

1. Cliquez sur **OK**.

   L’interface est créée dans le fichier portant le nom spécifié. De plus, la classe que vous avez sélectionnée implémente cette interface.

   - C# :

    ![Classe résultante (C#)](media/extractinterface-class-cs.png)
    ![Interface résultante (C#)](media/extractinterface-interface-cs.png)

   - Visual Basic :

    ![Classe résultante (Visual Basic)](media/extractinterface-class-vb.png)
    ![Interface résultante (Visual Basic)](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)