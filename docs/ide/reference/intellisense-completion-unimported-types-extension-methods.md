---
title: Saisie semi-automatique IntelliSense pour les types et les méthodes d’extension inimportés
description: Comment utiliser la saisie semi-automatique IntelliSense pour les types et les méthodes d’extension que vous n’avez pas encore importés avec une `using` directive.
ms.date: 07/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d6112bc3894424b9dfd3d060ed390960243b0f98
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87330986"
---
# <a name="intellisense-completion-for-unimported-types-and-extension-methods"></a>Saisie semi-automatique IntelliSense pour les types et les méthodes d’extension inimportés

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Ce qui suit :** IntelliSense fournit la saisie semi-automatique des types et des méthodes d’extension inimportés.

Dans les **cas suivants :** Vous souhaitez utiliser un type ou des méthodes d’extension qui ont déjà une dépendance dans votre projet, mais l’instruction using n’a pas encore été ajoutée à votre fichier. 

**Pourquoi :** Vous n’avez pas besoin d’ajouter manuellement l’instruction using à votre fichier.

## <a name="how-to"></a>Procédures

1. Une fois que vous avez commencé à taper le nom d’un type ou d’une méthode d’extension qui a une dépendance dans votre projet, IntelliSense vous donne des suggestions. L’espace de noms conteneur des éléments des espaces de noms qui ne sont pas importés est indiqué comme suffixe.

   > [!TIP]
   > Vous pouvez afficher/masquer les éléments des espaces de noms non importés à la demande, à l’aide du **bouton de développement (Alt + A)** qui apparaît en bas à gauche de la liste de saisie semi-automatique. Pour modifier le comportement par défaut, accédez à **Outils**  >  **options**  >  **éditeur de texte**  >  **C#**  /  de**base**  >  **IntelliSense** et recherchez **afficher les éléments des espaces de noms non importés**.

2. Sélectionner et valider un élément non importé. 

   L’instruction using sera automatiquement ajoutée à votre fichier.

   ![Autocomplétion IntelliSense pour les types non importés](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Voir aussi

- [IntelliSense](../using-intellisense.md)
- [Refactorisation](../refactoring-in-visual-studio.md)
