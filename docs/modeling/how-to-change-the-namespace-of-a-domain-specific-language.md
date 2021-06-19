---
title: 'Comment : modifier l’espace de noms d’un langage spécifique à un domaine'
description: Fournit des informations sur la modification de l’espace de noms d’un langage spécifique à un domaine.
ms.date: 10/31/2018
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- Domain-Specific Language, namespace
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: db9043c2a4c5abd19c839d2586709412d7607019
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387305"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Comment : modifier l’espace de noms d’un langage spécifique à un domaine

Vous pouvez modifier l’espace de noms d’un langage spécifique à un domaine. Apportez les modifications dans l' **Explorateur DSL**, dans les propriétés du projet de package DSL et dans les informations de l’assembly.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Pour modifier l’espace de noms d’un langage spécifique à un domaine

1. Dans l' **Explorateur DSL**, sélectionnez le nœud **DSL** .

2. Dans la fenêtre **Propriétés** , modifiez la propriété **espace de noms** .

3. Enregistrez la solution et transformez les modèles.

4. Dans le menu **projet** , choisissez **Propriétés DSL**.

   Les propriétés de votre projet s’affichent.

5. Sélectionnez l'onglet **Application**.

6. Remplacez la valeur de la propriété **espace de noms par défaut par** le nouveau nom de l’espace de noms.

7. Si vous souhaitez également modifier le nom de l’assembly, modifiez la **propriété nom de l’assembly.**

8. Si vous avez modifié le nom de l’assembly, ouvrez DslPackage\Package.tt et mettez à jour cette ligne :

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Si vous avez écrit du code personnalisé, veillez à modifier les références de l’espace de noms et de la classe dans les fichiers de code.

10. Réinitialisez l’instance expérimentale de Visual Studio.

    1. Supprimer **\Utilisateurs \\**_{votre nom}_**\AppData\Local\Microsoft\VisualStudio \\ \* exp**.

    2. Dans le menu **Démarrer** de Windows, choisissez **tous les programmes**  >  **Microsoft Visual Studio outils du kit de développement logiciel (SDK) 2010**  >    >  **Réinitialiser l’instance expérimentale**.

11. Dans le menu **générer** , choisissez **régénérer la solution**.

## <a name="see-also"></a>Voir aussi

[Glossaire des outils de langage spécifique à un domaine](/previous-versions/bb126564(v=vs.100))