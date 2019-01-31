---
title: Créer un projet de test unitaire
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e90aa1f8fe13bc7ee99f3ac20b1813ca2a6c9672
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996812"
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