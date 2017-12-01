---
title: "Générer Equals et GetHashCode, méthode remplacements - génération de Code (c#) | Documents Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.openlocfilehash: 88ebbeed4af1d0ea79a27ff21f7ae38ec8c252c1
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2017
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Générer Equals et GetHashCode, méthode remplace en c# #

**Ce que :** vous permet de générer **est égal à** et **GetHashCode** méthodes.

**Quand :** générer ces substitutions lorsque vous disposez d’un type qui représente une « valeur » doit être comparée en fonction de certains champs, au lieu de par l’emplacement de l’objet en mémoire.

**Pourquoi :** si vous implémentez un type valeur, vous devez envisager de substituer la méthode Equals afin d’améliorer les performances sur l’implémentation par défaut de la méthode Equals sur ValueType.

Si vous implémentez un type référence, vous devez envisager de substituer la méthode Equals si votre type ressemble à un type de base, telles que le Point, String, BigNumber et ainsi de suite.

Substituez la méthode GetHashCode pour permettre à un type de fonctionner correctement dans une table de hachage. Lire plus d’informations sur [opérateurs d’égalité](/dotnet/standard/design-guidelines/equality-operators).

**Comment faire :**

1. Placez votre curseur dans votre déclaration de type.

   ![Code en surbrillance](media/overrides_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **Equals(object) de générer** ou **générer Equals et GetHashCode** à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Avec le bouton droit et sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **Equals(object) de générer** ou **générer Equals et GetHashCode** à partir de la fenêtre d’aperçu menu contextuel.
     * Cliquez sur le bouton ![Ampoule](media/bulb.png) icône qui apparaît dans la marge de gauche, si le curseur de texte se trouve déjà sur la ligne de la déclaration de type.

   ![Génération d’un aperçu des remplacements](media/overrides_preview.png)

1. Sélectionner les membres que vous souhaitez générer les substitutions de méthodes pour :

    ![Générer des remplacements de la boîte de dialogue](media/overrides_dialog.png)

    > [!TIP]
    > Vous pouvez également choisir de générer des opérateurs à partir de cette boîte de dialogue en utilisant les cases à cocher sous la liste des membres.

1. Equals et GetHashCode remplacements seront générés avec les implémentations par défaut automatique.

   ![Générer le résultat de la méthode](media/overrides_result.png)

## <a name="see-also"></a>Voir aussi

[Génération de code (C#)](../code-generation-csharp.md)  
[Aperçu des modifications](../../ide/preview-changes.md)
