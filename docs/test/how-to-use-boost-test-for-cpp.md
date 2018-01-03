---
title: Guide pratique pour utiliser Boost.Test pour C++ dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0710a8-8e8a-4f6e-8415-5ab3eb830079
caps.latest.revision: "14"
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af55f9f124b2ec609c4f0a590e7c2fab738624d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-boosttest-for-c-in-visual-studio"></a>Guide pratique pour utiliser Boost.Test pour C++ dans Visual Studio
Dans **Visual Studio 2017 version 15.5** et ultérieur, Boost.Test est intégré dans l’IDE Visual Studio comme composant de la charge de travail **Développement Desktop en C++**. Pour l’installer sur votre machine, ouvrez le programme d’installation de Visual Studio et recherchez **Adaptateur Boost.Test** sous la liste des composants de la charge de travail :

![Installer Boost.Test](media/cpp-boost-component.png "Installer Boost.Test pour C++")

## <a name="install-boost"></a>Installer Boost

 Boost.Test nécessite [Boost](http://www.boost.org/)! Si Boost n’est pas installé, nous vous recommandons d’utiliser le gestionnaire de package Vcpkg. 

1. Suivez les instructions de [Vcpkg : un gestionnaire de package C++ pour Windows](/cpp/vcpkg) pour installer vcpkg (si vous ne l’avez pas déjà).
2. Exécutez `vcpkg install boost` pour installer les bibliothèques Boost.
3. Exécutez la commande `vcpkg integrate install` pour configurer Visual Studio avec la bibliothèque, et inclure les chemins des fichiers d’en-tête et des fichiers binaires de Boost. 

## <a name="create-a-project-for-your-tests"></a>Créer un projet pour vos tests
Dans Visual Studio 2017 version 15.5, aucun modèle de projet ou d’élément de test préconfiguré n’est disponible pour Boost.Test. Vous devez donc créer un projet d’application de console pour y placer vos tests. Des modèles de test pour Boost.Test sont prévus pour une version future de Visual Studio. 

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution et choisissez **Ajouter | Nouveau projet**. 
2. Dans le volet gauche, choisissez **Windows Desktop**, puis **Application console Windows** dans le volet central. 
3. Nommez le projet, puis cliquez sur **OK**. 

## <a name="add-include-directives"></a>Ajouter des directives include
Dans votre fichier .cpp de test, ajoutez les directives `#include` nécessaires pour rendre les types et les fonctions de votre programme visibles par le code de test. En règle générale, le programme est un niveau au-dessus dans l’arborescence des dossiers. Si vous tapez `#include "../"`, une fenêtre IntelliSense apparaît et vous permet de sélectionner le chemin complet du fichier d’en-tête.

![Ajouter des directives #include](media/cpp-gtest-includes.png "Ajouter des directives include dans le fichier .cpp de test")

Au minimum, vous devez inclure la [variante d’en-tête unique de Boost.Test](http://www.boost.org/doc/libs/1_48_0/libs/test/doc/html/utf/user-guide/usage-variants/single-header-variant.html) avec `#include <path>/unit_test.hpp` et définir `BOOST_TEST_MODULE`. L’exemple suivant est suffisant pour que le test soit découvrable dans **l’Explorateur de tests** :

```cpp
#include "stdafx.h"
#define BOOST_TEST_MODULE MyTest
#include <boost/test/included/unit_test.hpp>
#include "../MyProgram/MyClass.h" // project being tested
#include <string>

BOOST_AUTO_TEST_CASE(my_boost_test)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual();
    BOOST_CHECK(name == mc.GetName());
}
```

## <a name="write-and-run-tests"></a>Écrire et exécuter des tests
Vous êtes maintenant prêt à écrire et à exécuter des tests Boost. Pour plus d’informations sur les macros de test, consultez la [documentation de la bibliothèque de tests Boost](http://www.boost.org/doc/libs/1_38_0/libs/test/doc/html/index.html). Pour plus d’informations sur la découverte, l’exécution et le regroupement de vos tests avec **l’Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Voir aussi
[Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)


  







