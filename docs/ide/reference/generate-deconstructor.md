---
title: Action rapide Générer un constructeur
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour générer immédiatement le stub de méthode pour un nouveau déconstructeur.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ff2ac7682eff1c3da0597a95945a6a0b016d9213
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617251"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Générer un constructeur dans Visual Studio

Cette génération de code s’applique à :

- C#

**Ce qui suit :** Vous permet de générer immédiatement le stub de méthode pour un nouveau deconstructeur.

Dans les **cas suivants :** Vous voulez décomposer correctement votre type automatiquement.

**Pourquoi :** Vous pouvez taper manuellement un deconstructeur, mais cette fonctionnalité génère le stub pour vous avec les paramètres de sortie corrects.

## <a name="generate-a-deconstructor"></a>Générer un déconstructeur

1. Déclarez un nouveau type en spécifiant les paramètres de sortie de votre choix. Cette déclaration provoque une erreur si aucune instance de déconstruction correspondante n’est trouvée.

   ![Erreur liée à un déconstructeur manquant](media/deconstruct.png)

2. Exécutez l’une des étapes suivantes :

   - **Clavier**
      - Placez le curseur dans votre déclaration, puis sélectionnez Ctrl+. pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Sélectionnez l' :::image type="icon" source="media/screwdriver.png"::: icône qui s’affiche dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne vide dans la classe.

      ![Générer un déconstructeur (correctif de code)](media/deconstruct-codefix.png)

3. Sélectionnez **Générer la méthode 'MyInternalClass.Deconstruct'** pour générer le déconstructeur.

   ![Code de déconstructeur résultant](media/deconstruct-result.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)