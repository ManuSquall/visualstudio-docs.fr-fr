---
title: Guide pratique pour utiliser Google Test pour C++
description: Utilisez Google Test pour créer des tests unitaires C++ dans Visual Studio.
ms.date: 05/06/2017
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: a338b6f62aee6ec342ef6a16abec71cb6a833bc0
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042962"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Guide pratique pour utiliser Google Test pour C++ dans Visual Studio

Dans Visual Studio 2017 et ultérieur, Google Test est intégré dans l’IDE Visual Studio comme composant par défaut de la charge de travail **Développement Desktop en C++**. Pour vérifier qu’il est installé sur votre machine, ouvrez Visual Studio Installer et recherchez Google Test sous la liste des composants de charge de travail :

![Installation de Google Test](media/cpp-google-component.png)

::: moniker range=">=vs-2019"

## <a name="add-a-google-test-project-in-visual-studio-2019"></a>Ajouter un projet Google Test dans Visual Studio 2019

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution et choisissez **Ajouter** > **nouveau projet**.
2. Définissez **Langage** sur **C++** et tapez **test** dans la zone de recherche. Dans la liste des résultats, choisissez **Projet Google Test**.
3. Nommez le projet de test, puis cliquez sur **OK**.

![Nouveau projet Google Test](media/vs-2019/cpp-gtest-new-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

## <a name="add-a-google-test-project-in-visual-studio-2017"></a>Ajouter un projet Google Test dans Visual Studio 2017

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution et choisissez **Ajouter** > **nouveau projet**.
2. Dans le volet gauche, choisissez **Visual C++** > **test** , puis choisissez **Google test projet** dans le volet central.
3. Nommez le projet de test, puis cliquez sur **OK**.

![Nouveau projet Google Test](media/cpp-gtest-new-project.png)

::: moniker-end

## <a name="configure-the-test-project"></a>Configurer le projet de test

Dans la boîte de dialogue **Configuration du projet de test** qui s’affiche, vous pouvez choisir le projet à tester. Quand vous choisissez un projet, Visual Studio ajoute une référence au projet sélectionné. Si vous ne choisissez aucun projet, vous devez ajouter manuellement des références au(x) projet(s) que vous voulez tester. Pour le choix entre les liaisons statiques et dynamiques pour les fichiers binaires Google Test, les considérations sont les mêmes que pour n’importe quel programme C++. Pour plus d’informations, consultez [DLL dans Visual C++](/cpp/build/dlls-in-visual-cpp).

![Configurer le projet Google Test](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Définir des options supplémentaires

Dans le menu principal, choisissez **Outils**  >  **options**  >  **adaptateur de test pour Google test** pour définir des options supplémentaires. Pour plus d’informations sur ces paramètres, consultez la documentation de Google Test.

![Paramètres du projet Google Test](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Ajouter des directives include

Dans votre fichier test *. cpp* , ajoutez toutes les `#include` directives nécessaires pour rendre les types et les fonctions de votre programme visibles au code de test. En règle générale, le programme est un niveau au-dessus dans l’arborescence des dossiers. Si vous tapez `#include "../"`, une fenêtre IntelliSense apparaît et vous permet de sélectionner le chemin complet du fichier d’en-tête.

![Ajouter des directives #include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Écrire et exécuter des tests

Vous êtes maintenant prêt à écrire et à exécuter des tests Google. Pour plus d’informations sur les macros de test, consultez le [Google test Primer](https://github.com/google/googletest/blob/master/docs/primer.md) . Pour plus d’informations sur la découverte, l’exécution et le regroupement de vos tests avec **l’Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Voir aussi

[Écrire des tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)
