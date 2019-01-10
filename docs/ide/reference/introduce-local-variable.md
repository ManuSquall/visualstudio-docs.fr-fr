---
title: Introduire une variable locale
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 42d3f7da59fc64e70ab453a6dd1f57d95871b684
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968681"
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
      - Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

   ![Introduire un aperçu local](media/local-preview-cs.png)

3. Sélectionnez **Introduire un élément local pour (toutes les occurrences de '*expression*'** à partir du menu déroulant.

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
- [Aperçu des modifications](../../ide/preview-changes.md)