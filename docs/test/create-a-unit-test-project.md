---
title: Créer un projet de test unitaire dans Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d49748be3067ac2bbb6df9016883cb7be0f48f89
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586858"
---
# <a name="create-a-unit-test-project"></a>Créer un projet de test unitaire

Les tests unitaires reflètent souvent la structure du code testé. Par exemple, un projet de test unitaire est créé pour chaque projet de code du produit. Le projet de test peut se trouver dans la même solution que le code de production, ou dans une solution distincte. Vous pouvez avoir plusieurs projets de test unitaire dans une solution.

> [!NOTE]
> L’emplacement des tests unitaires du code natif et la structure du projet de test peuvent être différents de la structure décrite dans cette rubrique. Pour plus d’informations, consultez [Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Pour créer un projet de test unitaire :

1.  Dans le menu **Fichier**, choisissez **Nouveau**, puis **Projet** (**Ctrl**+**Maj**+**N**).

2.  Dans la boîte de dialogue **Nouveau projet**, développez le nœud **Installé**, choisissez le langage que vous voulez utiliser pour votre projet de test, puis sélectionnez **Test**.

3.  Pour utiliser l’une des infrastructures de tests unitaires Microsoft, choisissez **Projet de test unitaire** dans la liste des modèles de projet. Sinon, choisissez le modèle de projet de l’infrastructure de tests unitaires que vous souhaitez utiliser. Pour tester le projet Accounts de notre exemple, nommez le projet **AccountsTests**.

4.  Dans votre projet de test unitaire, ajoutez une référence au code testé.  Voici comment créer la référence à un projet de code dans la même solution :

    1.  Sélectionnez le projet dans **l’Explorateur de solutions**.

    2.  Dans le menu **Projet** , choisissez **Ajouter une référence**.

    3.  Dans la boîte de dialogue **Gestionnaire de références**, ouvrez le nœud **Solution** et choisissez **Projets**. Vérifiez le nom du projet de code et fermez la boîte de dialogue.

5.  Si le code que vous souhaitez tester se trouve à un autre emplacement, consultez [Gestion des références dans un projet](../ide/managing-references-in-a-project.md) pour plus d’informations sur l’ajout de références.

## <a name="next-steps"></a>Étapes suivantes

 Consultez l’une des sections suivantes :

**Écriture de tests unitaires**

- [Tests unitaires sur votre code](../test/unit-test-your-code.md)

- [Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)

- [Utiliser le framework MSTest dans les tests unitaires](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Exécution de tests unitaires**

- [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)