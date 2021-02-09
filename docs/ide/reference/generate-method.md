---
title: Générer une méthode
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour ajouter immédiatement une méthode à une classe.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c6f4a25e3cda10e74c344cb7eef879b78f60a1de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903903"
---
# <a name="generate-a-method-in-visual-studio"></a>Générer une méthode dans Visual Studio

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet d’ajouter immédiatement une méthode à une classe.

**Quand :** vous introduisez une nouvelle méthode et souhaitez la déclarer correctement, automatiquement.

**Pourquoi :** vous pouvez déclarer la méthode et ses paramètres avant de l’utiliser, mais cette fonctionnalité le générera automatiquement la déclaration.

## <a name="how-to"></a>Procédures

1. Placez votre curseur sur la ligne présentant un trait rouge ondulé. Celui-ci indique une méthode qui n’existe pas encore.

   - C# :

       ![Code C# mis en surbrillance](media/method-highlight-cs.png)

   - Visual Basic :

       ![Code VB mis en surbrillance](media/method-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![ampoule d’erreur](media/error-bulb.png) qui apparaît.
      - Cliquez sur l’icône ![ampoule d’erreur](media/error-bulb.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

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
