---
title: Introduire une variable locale
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 14a595de3b80635ad6974f2abb94bd9645d5a7f7
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55483807"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Introduire une variable locale dans Visual Studio

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** Vous permet de générer immédiatement une variable locale pour remplacer une expression existante.

**Quand :** Vous disposez d’un code pouvant être facilement réutilisé ultérieurement s’il figurait dans une variable locale.

**Pourquoi :** Vous pouvez copier et coller le code plusieurs fois pour l’utiliser à différents emplacements. Toutefois, il est préférable d’effectuer l’opération une seule fois, d’enregistrer le résultat dans une variable locale, puis d’utiliser cette variable locale au gré des besoins.

## <a name="how-to"></a>Procédure

1. Mettez en surbrillance l’expression que vous souhaitez assigner à une nouvelle variable locale.

   - C# :

       ![Code C# mis en surbrillance](media/local-highlight-cs.png)

   - Visual Basic :

       ![Code VB mis en surbrillance](media/local-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Cliquez sur l’icône ![de tournevis](media/screwdriver.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne avec l’expression en surbrillance.

   ![Introduire un aperçu local](media/local-preview-cs.png)

3. Sélectionnez **Introduire un élément local pour (toutes les occurrences) de « expression »** dans le menu déroulant.

   > [!TIP]
   > Utilisez le lien **Aperçu des modifications** en bas de la fenêtre d’aperçu [pour voir tous les changements](../../ide/preview-changes.md) qui seront apportés avant d’effectuer votre sélection.

   La variable locale est créée avec le type déduit de son utilisation. Renommez la nouvelle variable locale.

   - C# :

       ![Résultat de l’implémentation de l’interface (C#)](media/local-result-cs.png)

   - Visual Basic :

       ![Résultat de l’implémentation de l’interface (VB)](media/local-result-vb.png)

   > [!NOTE]
   > Vous pouvez utiliser l’option de menu **...toutes les occurrences de...** pour remplacer chaque instance de l’expression sélectionnée, et pas seulement celle que vous avez spécifiquement mise en surbrillance.

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des changements](../../ide/preview-changes.md)