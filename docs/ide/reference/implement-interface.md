---
title: Implémenter une interface
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour générer immédiatement le code requis pour implémenter une interface.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 37adee082f5356180b4e1d58007db48a7f9bb60e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852490"
---
# <a name="implement-an-interface-in-visual-studio"></a>Implémenter une interface dans Visual Studio

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de générer immédiatement le code requis pour implémenter une interface.

**Quand :** vous voulez hériter d’une interface.

**Pourquoi :** vous pouvez implémenter manuellement tous les éléments d’une interface un par un, mais cette fonctionnalité générera automatiquement toutes les signatures de la méthode.

## <a name="how-to"></a>Procédures

1. Placez votre curseur sur la ligne présentant un trait rouge ondulé. Celui-ci indique que vous avez référencé une interface, mais que vous n’avez pas implémenté tous les membres nécessaires.

   - C# :

       ![Code C# mis en surbrillance](media/interface-highlight-cs.png)

   - Visual Basic :

       ![Code VB mis en surbrillance](media/interface-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![ampoule d’erreur](media/error-bulb.png) qui apparaît.
      - Cliquez sur l’icône ![ampoule d’erreur](media/error-bulb.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

3. Sélectionnez **Implémenter l’interface** à partir du menu déroulant.

   ![Implémenter l’interface (préversion)](media/interface-preview-cs.png)

   > [!TIP]
   > - Utilisez le lien **Aperçu des modifications** en bas de la fenêtre d’aperçu [pour voir tous les changements](../../ide/preview-changes.md) qui seront apportés avant d’effectuer votre sélection.
   > - Utilisez les liens **Document**, **Projet** et **Solution** en bas de la fenêtre d’aperçu pour créer les signatures de méthode appropriées sur plusieurs classes qui implémentent l’interface.

   Les signatures de la méthode de l’interface sont créées et prêtes à être implémentées.

   - C# :

       ![Résultat de l’implémentation de l’interface (C#)](media/interface-result-cs.png)

   - Visual Basic :

       ![Résultat de l’implémentation de l’interface (VB)](media/interface-result-vb.png)

   > [!TIP]
   > (C# uniquement) Utilisez l’option **Implémenter l’interface explicitement** pour faire précéder chaque méthode générée du nom de l’interface et éviter ainsi les conflits de noms.
   >
   > ![Résultat de l’action Implémenter l'interface explicitement](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
