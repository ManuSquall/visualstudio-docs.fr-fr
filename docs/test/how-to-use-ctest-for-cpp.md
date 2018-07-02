---
title: Guide pratique pour utiliser CTest pour C++ dans Visual Studio
ms.date: 11/07/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 98e258c2547bbd3cd1b87d289bf643956acfdb1d
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751031"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Guide pratique pour utiliser CTest pour C++ dans Visual Studio

CMake (qui comprend CTest) est intégré par défaut à l’IDE de Visual Studio sous forme de composant de la charge de travail **Développement Desktop en C++**. Pour l’installer sur votre ordinateur, ouvrez le programme Visual Studio Installer, cliquez sur le bouton **Modifier** et cochez [Outils CMake pour Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) sous la liste des composants de la charge de travail.

## <a name="to-write-tests"></a>Écrire des tests

La prise en charge de CMake dans Visual Studio n’implique pas le système de projet de Visual Studio. Par conséquent, écrivez et configurez les tests CTest comme vous le feriez dans n’importe quel environnement CMake. Pour plus d’informations sur l’utilisation de CMake dans Visual Studio, consultez la page [Outils CMake pour Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

## <a name="to-run-tests-visual-studio-2017-version-156"></a>Exécuter des tests (Visual Studio 2017 version 15.6)

Dans la version 15.6 de Visual Studio 2017, CTest est entièrement intégré à **l’Explorateur de tests** et prend également en charge les infrastructures de tests unitaires Google et Boost. Celles-ci sont incluses par défaut en tant que composants de la charge de travail **Développement Desktop en C++**. Toutefois, si vous mettez à niveau un projet à partir d’une version antérieure de Visual Studio, vous devrez peut-être les installer à l’aide du programme Visual Studio Installer.

L’illustration suivante montre les résultats d’une exécution de CTest réalisée avec l’infrastructure Google Test :

![CTest avec Google Test Framework dans VS2017 15.6](media/ctest-test-explorer.png)

Si vous utilisez CTest sans les adaptateurs Google ou Boost, les résultats s’afficheront au niveau CTest plutôt qu’au niveau de chaque méthode de test. Il est possible de déboguer et de lancer pas à pas les exécutables CTest uniquement, mais les rapports des appels de procédure sur les tests individuels ne sont pas pris en charge.

## <a name="to-run-tests-visual-studio-2017-version-155"></a>Exécuter des tests (Visual Studio 2017 version 15.5)

Dans la **version 15.5 de Visual Studio 2017**, CTest n’est pas intégré à **l’Explorateur de tests**. Vous pouvez exécuter vos tests à partir du menu principal de CMake ou du menu contextuel sur un fichier **CMakeLists.txt** dans **l’Explorateur de solutions**. Les résultats des tests sont dirigés vers la **fenêtre Sortie** de Visual Studio.

![Exécuter des tests CTest dans VS2017 15.5](media/cpp-cmake-run-tests.png)

## <a name="see-also"></a>Voir aussi

[Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)