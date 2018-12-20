---
title: Générer une méthode
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 1e5cf156c6c17e8a9bf1fb9f40f75c1e72b7be94
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057176"
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
      - Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![Ampoule](media/bulb-cs.png) qui apparaît.
      - Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

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