---
title: 'Comment : modifier l’espace de noms d’un langage spécifique à un domaine'
ms.date: 10/31/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b64a61c02f44db0ce70b758331d0d70f7bb8014d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653765"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Comment : modifier l’espace de noms d’un langage spécifique à un domaine

Vous pouvez modifier l’espace de noms d’un langage spécifique à un domaine. Apportez les modifications dans l' **Explorateur DSL**, dans les propriétés du projet de package DSL et dans les informations de l’assembly.

## <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Pour modifier l’espace de noms d’un langage spécifique à un domaine

1. Dans l' **Explorateur DSL**, sélectionnez le nœud **DSL** .

2. Dans la fenêtre **Propriétés** , modifiez la propriété **espace de noms** .

3. Enregistrez la solution et transformez les modèles.

4. Dans le menu **projet** , choisissez **Propriétés DSL**.

   Les propriétés de votre projet s’affichent.

5. Sélectionnez l’onglet **application** .

6. Remplacez la valeur de la propriété **espace de noms par défaut par** le nouveau nom de l’espace de noms.

7. Si vous souhaitez également modifier le nom de l’assembly, modifiez la **propriété nom de l’assembly.**

8. Si vous avez modifié le nom de l’assembly, ouvrez DslPackage\Package.tt et mettez à jour cette ligne :

   `string dslAssembly = "YourDSLassembly.Dsl.dll";`

9. Si vous avez écrit du code personnalisé, veillez à modifier les références de l’espace de noms et de la classe dans les fichiers de code.

10. Réinitialisez l’instance expérimentale de Visual Studio.

    1. Supprimez **\utilisateurs \\** _{your name}_ **\AppData\Local\Microsoft\VisualStudio \\ \*Exp**.

    2. Dans le menu **Démarrer** de Windows, choisissez **tous les programmes**  > **Microsoft Visual Studio Kit de développement logiciel (SDK) 2010**  > **Outils**  > **Réinitialiser l’instance expérimentale**.

11. Dans le menu **générer** , choisissez **régénérer la solution**.

## <a name="see-also"></a>Voir aussi

[Glossaire des outils de langage spécifique à un domaine](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)