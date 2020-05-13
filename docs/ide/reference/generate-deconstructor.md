---
title: Action rapide Générer un constructeur
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5a3a89d15d05b44575fede98d3043d706b24c1d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531885"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Générer un constructeur dans Visual Studio

Cette génération de code s’applique à :

- C#

**Quoi :** Vous permet de générer immédiatement le talon de méthode pour un nouveau déconstructeur.

**Quand :** Vous souhaitez déconstruire correctement votre type automatiquement.

**Pourquoi:** Vous pouvez taper manuellement un déconstructeur, mais cette fonctionnalité génère le talon pour vous avec les paramètres corrects.

## <a name="generate-a-deconstructor"></a>Générer un déconstructeur

1. Déclarez un nouveau type en spécifiant les paramètres de sortie de votre choix. Cette déclaration provoque une erreur si aucune instance de déconstruction correspondante n’est trouvée.

   ![Erreur liée à un déconstructeur manquant](media/deconstruct.png)

2. Exécutez l’une des étapes suivantes :

   - **Clavier**
      - Placez le curseur dans votre déclaration, puis sélectionnez Ctrl+. pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Sélectionnez ![Tournevis](media/screwdriver.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne vide dans la classe.

      ![Générer un déconstructeur (correctif de code)](media/deconstruct-codefix.png)

3. Sélectionnez **Générer la méthode 'MyInternalClass.Deconstruct'** pour générer le déconstructeur.

   ![Code de déconstructeur résultant](media/deconstruct-result.png)

## <a name="see-also"></a>Voir aussi

- [Génération de codes](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)