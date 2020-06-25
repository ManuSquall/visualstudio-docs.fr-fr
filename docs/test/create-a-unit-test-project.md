---
title: Créer un projet de test unitaire
ms.date: 01/29/2019
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ffa19fb9dc49d6286ef3f54c51d89043445f18ba
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288713"
---
# <a name="create-a-unit-test-project"></a>Créer un projet de test unitaire

Les tests unitaires reflètent souvent la structure du code testé. Par exemple, un projet de test unitaire est créé pour chaque projet de code du produit. Le projet de test peut se trouver dans la même solution que le code de production, ou dans une solution distincte. Vous pouvez avoir plusieurs projets de test unitaire dans une solution.

> [!NOTE]
> L’emplacement des tests unitaires du code natif et la structure du projet de test peuvent être différents de la structure décrite dans cet article. Pour plus d’informations, consultez [écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Pour créer un projet de test unitaire

1. Dans le menu **Fichier**, choisissez **Nouveau** > **Projet** ou appuyez sur **Ctrl**+**Maj**+**N**.

::: moniker range="vs-2017"

2. Dans la boîte de dialogue **nouveau projet** , développez le nœud **installé** , choisissez la langue que vous souhaitez utiliser pour votre projet de test, puis choisissez **test**.

3. Sélectionnez le modèle de projet pour l’infrastructure de test que vous voulez utiliser, par exemple **Projet de test MSTest** ou **Projet de test NUnit**. Nommez le projet, puis choisissez **OK**.

   ![Modèles de projet de test dans Visual Studio 2017](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Dans la page **Créer un projet**, tapez **test unitaire** dans la zone de recherche. Sélectionnez le modèle de projet pour l’infrastructure de test que vous voulez utiliser, par exemple **Projet de test MSTest** ou **Projet de test NUnit**, puis choisissez **Suivant**.

   ![Modèles de projet de test dans Visual Studio 2019](media/vs-2019/test-project-templates.png)

3. Dans la page **Configurer votre nouveau projet**, entrez un nom pour le projet, puis choisissez **Créer**.

::: moniker-end

4. Dans votre projet de test unitaire, ajoutez une référence au code testé. Pour ajouter une référence à un projet de code dans la même solution :

   1. Sélectionnez le projet de test dans **l’Explorateur de solutions**.

   2. Dans le menu **projet** , choisissez **Ajouter une référence**.

   3. Dans **Gestionnaire de références**, sélectionnez le nœud **Solution** sous **Projets**. Sélectionnez le projet de code que vous voulez tester, puis sélectionnez **OK**.

   Si le code que vous voulez tester se trouve à un autre emplacement, consultez [Gestion des références dans un projet](../ide/managing-references-in-a-project.md) pour plus d’informations sur l’ajout d’une référence.

## <a name="next-steps"></a>Étapes suivantes

Consultez l’une des sections suivantes :

**Écriture de tests unitaires**

- [Test unitaire de votre code](../test/unit-test-your-code.md)

- [Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)

- [Utiliser le framework MSTest dans les tests unitaires](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Exécution de tests unitaires**

- [Exécuter des tests unitaires avec l'Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)
