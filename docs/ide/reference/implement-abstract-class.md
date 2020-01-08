---
title: Implémenter une classe abstraite
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6fcfdc06a055df28159f9d1ddc440aaf113f3264
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568904"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Implémenter une classe abstraite dans Visual Studio

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de générer immédiatement le code requis pour implémenter une classe abstraite.

**Quand :** vous voulez hériter d’une classe abstraite.

**Pourquoi :** vous pouvez implémenter manuellement tous les membres abstraits un par un, mais cette fonctionnalité générera automatiquement toutes les signatures de la méthode.

## <a name="how-to"></a>Procédure

1. Placez votre curseur sur la ligne présentant un trait rouge ondulé. Celui-ci indique que vous avez hérité d’une classe abstraite, mais que vous n’avez pas implémenté tous les membres nécessaires.

   - C# :

       ![Code C# mis en surbrillance](media/abstract-highlight-cs.png)

   - Visual Basic :

       ![Code VB mis en surbrillance](media/abstract-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![ampoule d’erreur](media/error-bulb.png) qui apparaît.
      - Cliquez sur l'onglet ![ampoule d’erreur](media/error-bulb.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

   ![Implémenter un aperçu de classe](media/abstract-preview-cs.png)

3. Sélectionnez **Implémenter une classe abstraite** dans le menu déroulant.

   > [!TIP]
   > - Utilisez le lien **Aperçu des modifications** en bas de la fenêtre d’aperçu [pour voir tous les changements](../../ide/preview-changes.md) qui seront apportés avant d’effectuer votre sélection.
   > - Utilisez les liens **Document**, **Projet** et **Solution** en bas de la fenêtre d’aperçu pour créer les signatures de méthode appropriées sur plusieurs classes qui héritent de la classe abstraite.

   Les signatures de la méthode abstraite sont créées et prêtes à être implémentées.

   - C# :

       ![Résultat de l’action Implémenter une classe (C#)](media/abstract-result-cs.png)

   - Visual Basic :

       ![Résultat de l’action Implémenter une classe (VB)](media/abstract-result-vb.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
