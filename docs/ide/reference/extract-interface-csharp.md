---
title: "Extraire une interface dans C# | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 0e763bacb6d900fea251b3c41d33fb464479f2c4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="extract-an-interface-in-c"></a>Extraire une interface dans C# #

**Quoi :** vous permet de créer une interface en utilisant les membres existants d’une classe, structure ou interface.

**Quand :** vous disposez de plusieurs classes, structures ou interfaces avec des méthodes qui peuvent être mises à la disposition et utilisées par d’autres classes, structures ou interfaces.

**Pourquoi :** les interfaces sont d’excellentes constructions pour les conceptions orientées objet.  Imaginez des classes représentant différents animaux (chien, chat, oiseau) pouvant être associées à des méthodes courantes, par exemple Manger, Boire et Dormir.  Une interface comme IAnimal permettrait aux éléments Chien, Chat et Oiseai d’avoir la même « signature » pour ces méthodes.

**Comment :**

1. Mettez en surbrillance le nom de la classe sur laquelle exécuter l’action, ou placez le curseur quelque part dans le nom de classe.

   ![Code mis en surbrillance](media/extractinterface-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+R**, puis **Ctrl+I**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire l’interface** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Sélectionnez **Modifier > Refactoriser > Extraire l’interface**.
     * Cliquez avec le bouton droit sur le nom de la classe et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire l’interface** dans la fenêtre contextuelle d’aperçu.

1. Dans la boîte de dialogue **Extraire l’interface** qui s’affiche, entrez les informations demandées : ![Extraire l’interface](media/extractinterface-dialog-cs.png)
   | Champ | Description |
   | --- | --- |
   | **Nouveau nom d’interface** | Nom de l'interface à créer. Cette valeur est définie par défaut sur I*ClassName*, où *ClassName* représente le nom de la classe que vous avez sélectionné ci-dessus. |
   | **Nouveau nom de fichier** | Le nom du fichier qui sera généré et qui contiendra l’interface. Comme pour le nom de l’interface, cette valeur est définie par défaut sur I*ClassName*, où *ClassName* représente le nom de la classe que vous avez sélectionné ci-dessus. |
   | **Sélectionner les membres publics pour former l'interface** | Les éléments à extraire dans l’interface.  Vous pouvez sélectionner autant d’éléments que vous le souhaitez. |

1. Cliquez sur **OK**.

   L’interface sera immédiatement créée dans le fichier portant le nom spécifié.  En outre, la classe que vous avez sélectionnée implémentera désormais cette interface.

   ![Classe obtenue](media/extractinterface-class-cs.png)
   ![Interface obtenue](media/extractinterface-interface-cs.png)

## <a name="see-also"></a>Voir aussi

[Refactorisation](../refactoring-in-visual-studio.md)