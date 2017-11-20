---
title: "Extraire l’interface - refactorisation (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: db857fb1-3e22-46e2-b15a-56ef9f329235
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractinterface
dev_langs: VB
ms.openlocfilehash: 9616cae1282b992722f75eee091e2c9d271e85f6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="extract-an-interface-in-visual-basic"></a>Extraire une interface en Visual Basic
**Ce que :** vous permet de créer une interface à l’aide de membres existants à partir d’une classe, struct ou une interface.

**Quand :** vous disposez de plusieurs classes, structs ou interfaces avec des méthodes qui peuvent être rendus commune et utilisé par d’autres classes, structs ou des interfaces.

**Pourquoi :** Interfaces sont des constructions excellentes pour les conceptions orientée objet.  Imaginez que différents animaux (Dog, Cat, Bird) qui peuvent posséder des méthodes courantes, telles que de la mise en veille Eat, boisson, des classes.  À l’aide d’une interface comme IAnimal permettrait Dog, Cat et Bird ont le même « signature » pour ces méthodes.  

**Comment faire :**

1. Mettez en surbrillance le nom de la classe pour effectuer une action, ou simplement placer le curseur de texte quelque part dans le nom de classe.

   ![Code en surbrillance](media/extractinterface_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl + R**, puis **Ctrl + I**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **extraire l’Interface** à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Sélectionnez **Modifier > refactoriser > extraire l’Interface**.
     * Cliquez sur le nom de la classe, sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **extraire l’Interface** à partir du message de fenêtre d’aperçu.

1. Dans le **extraire l’Interface** boîte de dialogue qui s’affiche, entrez les informations demandées : ![extraire l’Interface](media/extractinterface_dialog.png)
   | Champ | Description |
   | --- | --- |
   | **Nouveau nom d’interface** | Le nom de l’interface doit être créé. Par défaut I*ClassName*, où *ClassName* est le nom de la classe que vous avez sélectionné ci-dessus. |
   | **Nouveau nom de fichier** | Le nom du fichier qui sera généré qui contiendra l’interface. Comme avec le nom d’interface par défaut I*ClassName*, où *ClassName* est le nom de la classe que vous avez sélectionné ci-dessus. |
   | **Sélectionner des membres publics pour former l’interface** | Éléments à extraire dans l’interface.  Vous pouvez sélectionner autant que vous le souhaitez. |

1. Cliquez sur **OK**.

   L’interface sera créé immédiatement dans le fichier portant le nom spécifié.  En outre, la classe que vous avez sélectionné implémentera maintenant cette interface.

   ![Classe qui en résulte](media/extractinterface_class.png)
   ![Interface résultante](media/extractinterface_interface.png)

## <a name="see-also"></a>Voir aussi
[Refactorisation (Visual Basic)](../refactoring-vb.md)