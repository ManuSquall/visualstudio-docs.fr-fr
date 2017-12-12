---
title: Guide pratique pour utiliser CTest pour C++ dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8b30934-5f38-4a18-8819-263e0733cdbe
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7e1d00460a4acf26f23c256f8eb0180360315a98
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Guide pratique pour utiliser CTest pour C++ dans Visual Studio
CMake (qui inclut CTest) est intégré dans l’IDE Visual Studio sous forme de composant de la charge de travail **Développement Desktop en C++**. Pour l’installer sur votre machine, ouvrez Visual Studio Installer et recherchez [Outils CMake pour Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) sous la liste des composants de la charge de travail.

La prise en charge de CMake dans Visual Studio n’implique pas la présence du système de projets Visual Studio. Par conséquent, écrivez et configurez les tests CTest comme vous le feriez dans n’importe quel environnement CMake. Pour plus d’informations sur l’utilisation de CMake dans Visual Studio, consultez [Outils CMake pour Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

Actuellement, CTest **Visual Studio 2017 version 15.5** n’est pas intégré à **l’Explorateur de tests**. Vous pouvez exécuter vos tests à partir du menu principal de CMake ou du menu contextuel sur un fichier **CMakeLists.txt** dans **l’Explorateur de solutions**. Les résultats des tests sont dirigés vers la **fenêtre Sortie** de Visual Studio.

![Exécuter des tests CTest](media/cpp-cmake-run-tests.png "Exécuter des tests CTest")


## <a name="see-also"></a>Voir aussi
[Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)


  







