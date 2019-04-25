---
title: Générer un champ, une propriété ou une variable locale
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a8373339f921c032e52c00b5c8a54e910e5a1c54
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790352"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Générer un champ, une propriété ou une variable locale dans Visual Studio

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** Vous permet de générer immédiatement le code d’un champ, d’une propriété ou d’une valeur locale non déclarée précédemment.

**Quand :** Vous introduisez un nouveau champ, une nouvelle propriété ou une nouvelle valeur locale lors de la saisie et que vous souhaitez correctement déclarer cet élément, automatiquement.

**Pourquoi :** Vous pouvez déclarer le champ, la propriété ou la valeur locale avant de l’utiliser, mais cette fonctionnalité générera automatiquement la déclaration et le type.

## <a name="how-to"></a>Procédure

1. Placez votre curseur sur la ligne présentant un trait rouge ondulé. Celui-ci indique un champ, une variable locale ou une propriété qui n’existe pas encore.

   - C# :

       ![Code C# mis en surbrillance](media/field-highlight-cs.png)

   - Visual Basic :

       ![Code VB mis en surbrillance](media/field-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![ampoule d’erreur](media/error-bulb.png) qui apparaît.
      - Cliquez sur le bouton ![ampoule d’erreur](media/error-bulb.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

      ![Aperçu de l’action Générer le champ/la propriété/la valeur locale](media/field-preview-cs.png)

3. Sélectionnez l’une des options de génération dans le menu déroulant.

   > [!TIP]
   > Utilisez le lien **Aperçu des modifications** en bas de la fenêtre d’aperçu [pour voir tous les changements](../../ide/preview-changes.md) qui seront apportés avant d’effectuer votre sélection.

   Le champ, la propriété ou la variable locale est créé avec le type déduit de son utilisation.

   - C# :

       ![Résultat de l’action Générer une méthode (C#)](media/field-result-cs.png)

   - Visual Basic :

       ![Résultat de l’action Générer une méthode (VB)](media/field-result-vb.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)