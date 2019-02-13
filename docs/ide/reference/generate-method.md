---
title: Générer une méthode
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d815b638033e16796c90a362207b820bfe7cc57d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933517"
---
# <a name="generate-a-method-in-visual-studio"></a>Générer une méthode dans Visual Studio

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** Vous permet d’ajouter immédiatement une méthode à une classe.

**Quand :** Vous introduisez une nouvelle méthode et souhaitez la déclarer correctement, automatiquement.

**Pourquoi :** Vous pouvez déclarer la méthode et ses paramètres avant de l’utiliser, mais cette fonctionnalité génère automatiquement cette déclaration.

## <a name="how-to"></a>Procédure

1. Placez votre curseur sur la ligne présentant un trait rouge ondulé. Celui-ci indique une méthode qui n’existe pas encore.

   - C# :

       ![Code C# mis en surbrillance](media/method-highlight-cs.png)

   - Visual Basic :

       ![Code VB mis en surbrillance](media/method-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![ampoule d’erreur](media/error-bulb.png) qui apparaît.
      - Cliquez sur le bouton ![ampoule d’erreur](media/error-bulb.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

      ![Générer un aperçu de méthode](media/method-preview-cs.png)

3. Sélectionnez **Générer une méthode** dans le menu déroulant.

   > [!TIP]
   > Utilisez le lien **Aperçu des modifications** en bas de la fenêtre d’aperçu [pour voir tous les changements](../../ide/preview-changes.md) qui seront apportés avant d’effectuer votre sélection.

   La méthode est créée avec les paramètres déduits de son utilisation.

   - C# :

       ![Résultat de l’action Générer une méthode (C#)](media/method-result-cs.png)

   - Visual Basic :

       ![Résultat de l’action Générer une méthode (VB)](media/method-result-vb.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)