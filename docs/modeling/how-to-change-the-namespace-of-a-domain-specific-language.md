---
title: 'Procédure : Modifier l’espace de noms d’un langage spécifique à un domaine'
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16fec4cf6150fe0711812d9fabe57fc667e36eef
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55949191"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Procédure : Modifier l’espace de noms d’un langage spécifique à un domaine

Vous pouvez modifier l’espace de noms d’un langage spécifique à un domaine. Apportez la modification dans le **Explorateur DSL**dans les propriétés du projet de Dsl Package et dans les informations de l’assembly.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Pour modifier l’espace de noms d’un langage spécifique à un domaine

1. Dans **Explorateur DSL**, sélectionnez le **Dsl** nœud.

2. Dans le **propriétés** fenêtre, de modifier le **Namespace** propriété.

3. Enregistrez la solution et transformer les modèles.

4. Sur le **projet** menu, choisissez **Dsl propriétés**.

   Les propriétés de votre projet s’affichent.

5. Sélectionnez le **Application** onglet.

6. Modifier le **par défaut d’espace de noms** propriété vers le nouveau nom de l’espace de noms.

7. Si vous souhaitez également modifier le nom de l’assembly, modifiez le **propriété Assembly name.**

8. Si vous avez modifié le nom d’Assembly, ouvrez DslPackage\Package.tt et mettre à jour cette ligne :

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Si vous avez écrit n’importe quel code personnalisé, veillez à modifier les références d’espace de noms et classe dans les fichiers de code.

10. Réinitialiser l’instance expérimentale de Visual Studio.

    1. Supprimer **\Users\\**_{nom de votre}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**.

    2. Sur le Windows **Démarrer** menu, choisissez **tous les programmes** > **Microsoft Visual Studio 2010 SDK** > **outils**  >  **Réinitialiser l’Instance expérimentale**.

11. Sur le **Build** menu, choisissez **régénérer la Solution**.

## <a name="see-also"></a>Voir aussi

[Glossaire des outils de langage spécifique à un domaine](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)