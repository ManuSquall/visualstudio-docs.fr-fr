---
title: Introduire une variable locale
description: Générer une variable locale pour remplacer une expression existante Sélectionnez l’expression, cliquez avec le bouton droit et choisissez le menu Actions rapides et refactorisations, puis sélectionnez Introduire un élément local pour (toutes les occurrences de) « expression ».
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0fbd5ed752b28cc3f8c0dd734ed2b3ce09e80b78
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568813"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Introduire une variable locale dans Visual Studio

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de générer immédiatement une variable locale pour remplacer une expression existante.

**Quand :** vous disposez d’un code pouvant être facilement réutilisé ultérieurement s’il figurait dans une variable locale.

**Pourquoi :** vous pouvez copier et coller le code plusieurs fois pour l’utiliser à différents emplacements. Toutefois, il est préférable d’effectuer l’opération une seule fois, d’enregistrer le résultat dans une variable locale, puis d’utiliser cette variable locale au gré des besoins.

## <a name="how-to"></a>Procédure

1. Mettez en surbrillance l’expression que vous souhaitez assigner à une nouvelle variable locale.

   - C# :

       ![Code C# mis en surbrillance](media/local-highlight-cs.png)

   - Visual Basic :

       ![Code VB mis en surbrillance](media/local-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Cliquez sur l'onglet ![Tournevis](media/screwdriver.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne avec l’expression en surbrillance.

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
