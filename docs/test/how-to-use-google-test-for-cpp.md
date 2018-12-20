---
title: Guide pratique pour utiliser Google Test pour C++
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 704d842aaf3ea5e3075939e4d52b042a4128b810
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060389"
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Guide pratique pour utiliser Google Test pour C++ dans Visual Studio
Dans **Visual Studio 2017 version 15.5** et ultérieur, Google Test est intégré dans l’IDE Visual Studio comme composant par défaut de la charge de travail **Développement Desktop en C++**. Pour vérifier qu’il est installé sur votre machine, ouvrez Visual Studio Installer et recherchez Google Test sous la liste des composants de charge de travail :

![Installation de Google Test](media/cpp-google-component.png)

## <a name="add-a-google-test-project-to-the-solution"></a>Ajouter un projet Google Test à la solution
1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution et choisissez **Ajouter** > **Nouveau projet**.
2. Dans le volet gauche, choisissez **Visual C++** > **Test**, puis **Projet Google Test** dans le volet central.
3. Nommez le projet de test, puis cliquez sur **OK**.

![Nouveau projet Google Test](media/cpp-gtest-new-project.png)

## <a name="configure-the-test-project"></a>Configurer le projet de test
Dans la boîte de dialogue **Configuration du projet de test** qui s’affiche, vous pouvez choisir le projet à tester. Quand vous choisissez un projet, Visual Studio ajoute une référence au projet sélectionné. Si vous ne choisissez aucun projet, vous devez ajouter manuellement des références au(x) projet(s) que vous voulez tester. Pour le choix entre les liaisons statiques et dynamiques pour les fichiers binaires Google Test, les considérations sont les mêmes que pour n’importe quel programme C++. Pour plus d’informations, consultez [DLL dans Visual C++](/cpp/build/dlls-in-visual-cpp).

 ![Configurer le projet Google Test](media/cpp-gtest-config.png)

## <a name="set-additional-options"></a>Définir des options supplémentaires
Dans le menu principal, choisissez **Outils** > **Options** > **Adaptateur de test pour Google Test** pour définir des options supplémentaires. Pour plus d’informations sur ces paramètres, consultez la documentation de Google Test.

 ![Paramètres du projet Google Test](media/cpp-gtest-settings.png)

## <a name="add-include-directives"></a>Ajouter des directives include
Dans le fichier *.cpp* de test, ajoutez les directives `#include` nécessaires pour rendre les types et les fonctions de votre programme visibles par le code de test. En règle générale, le programme est un niveau au-dessus dans l’arborescence des dossiers. Si vous tapez `#include "../"`, une fenêtre IntelliSense apparaît et vous permet de sélectionner le chemin complet du fichier d’en-tête.

![Ajouter des directives #include](media/cpp-gtest-includes.png)

## <a name="write-and-run-tests"></a>Écrire et exécuter des tests
Vous êtes maintenant prêt à écrire et à exécuter des tests Google. Pour plus d’informations sur les macros de test, consultez [Google Test Primer](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Pour plus d’informations sur la découverte, l’exécution et le regroupement de vos tests avec **l’Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Voir aussi
[Écrire des tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)
