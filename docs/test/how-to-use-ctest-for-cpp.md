---
title: Guide pratique pour utiliser CTest pour C++
description: Découvrez comment créer et exécuter des tests avec CTest, qui est intégré dans l’IDE de Visual Studio par défaut.
ms.custom: SEO-VS-2020
ms.date: 01/23/2020
ms.topic: how-to
ms.author: corob
manager: jmartens
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 23d235d4b18c9909868cf890e31d835b3f7ea948
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969280"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Guide pratique pour utiliser CTest pour C++ dans Visual Studio 2017 et ultérieur

CMake (qui comprend CTest) est intégré par défaut à l’IDE de Visual Studio sous forme de composant de la charge de travail **Développement Desktop en C++**. Si vous avez besoin de l’installer sur votre machine, ouvrez le programme Visual Studio Installer, cliquez sur le bouton **Développement Desktop en C++**, puis cliquez sur **Modifier**. Sélectionnez **Outils CMake C++ pour Windows** sous la liste des composants de la charge de travail.

## <a name="to-write-tests"></a>Écrire des tests

La prise en charge de CMake dans Visual Studio n’implique pas le système de projet de Visual Studio. Par conséquent, écrivez et configurez les tests CTest comme vous le feriez dans n’importe quel environnement CMake. Utilisez la `enable_testing()` commande pour activer le test et la `add_test()` `gtest_discover_tests()` commande ou pour ajouter un nouveau test. Pour en savoir plus sur CTest, consultez la [documentation de cmake](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest). 

Pour plus d’informations sur l’utilisation de CMake dans Visual Studio, consultez la page [Projets CMake dans Visual Studio](/cpp/build/cmake-projects-in-visual-studio).

## <a name="to-run-tests"></a>Pour exécuter des tests

CTest est entièrement intégré à l’**Explorateur de tests** et prend également en charge les infrastructures de tests unitaires Google et Boost. Celles-ci sont incluses par défaut en tant que composants de la charge de travail **Développement Desktop en C++**. Toutefois, si vous mettez à niveau un projet à partir d’une version antérieure de Visual Studio, vous devrez peut-être les installer à l’aide du programme Visual Studio Installer.

L’illustration suivante montre les résultats d’une exécution de CTest réalisée avec l’infrastructure Google Test :

![CTest avec Google Test Framework dans Visual Studio](media/ctest-test-explorer.png)

Si vous utilisez CTest sans les adaptateurs Google ou Boost, les résultats s’afficheront au niveau CTest plutôt qu’au niveau de chaque méthode de test. Il est possible de déboguer et de lancer pas à pas les exécutables CTest uniquement, mais les rapports des appels de procédure sur les tests individuels ne sont pas pris en charge.

## <a name="see-also"></a>Voir aussi

- [Écrire des tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)
