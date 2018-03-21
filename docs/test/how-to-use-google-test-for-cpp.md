---
title: Guide pratique pour utiliser Google Test pour C++ dans Visual Studio | Microsoft Docs
ms.date: 11/04/2017
ms.technology: vs-ide-test
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 35cc31bbe7a1d83270035217dc36fce5f3a8ab6d
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-use-google-test-for-c-in-visual-studio"></a>Guide pratique pour utiliser Google Test pour C++ dans Visual Studio
Dans **Visual Studio 2017 version 15.5** et ultérieur, Google Test est intégré dans l’IDE Visual Studio comme composant par défaut de la charge de travail **Développement Desktop en C++**. Pour vérifier qu’il est installé sur votre machine, ouvrez Visual Studio Installer et recherchez Google Test sous la liste des composants de charge de travail :

![Installer Google Test](media/cpp-google-component.png "Installer Google Test pour C++")

## <a name="add-a-google-test-project-to-the-solution"></a>Ajouter le projet Google Test à la solution
1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution et choisissez **Ajouter | Nouveau projet**.
2. Dans le volet gauche, choisissez **Visual C++ | Test**, puis choisissez **Projet Google Test** dans le volet central.
3. Nommez le projet de test, puis cliquez sur **OK**.

![Nouveau projet Google Test](media/cpp-gtest-new-project.png "Ajouter un nouveau projet Google Test")

## <a name="configure-the-test-project"></a>Configurer le projet de test
Dans la boîte de dialogue **Configuration du projet de test** qui s’affiche, vous pouvez choisir le projet à tester. Quand vous choisissez un projet, Visual Studio ajoute une référence au projet sélectionné. Si vous ne choisissez aucun projet, vous devez ajouter manuellement des références au(x) projet(s) que vous voulez tester. Pour le choix entre les liaisons statiques et dynamiques pour les fichiers binaires Google Test, les considérations sont les mêmes que pour n’importe quel programme C++. Pour plus d’informations, consultez [DLL dans Visual C++](/cpp/build/dlls-in-visual-cpp).

 ![Configurer un projet Google Test](media/cpp-gtest-config.png "Configurer un projet Google Test")

## <a name="set-additional-options"></a>Définir des options supplémentaires
Dans le menu principal, choisissez **Outils | Options | Adaptateur de test pour Google Test** pour définir des options supplémentaires. Pour plus d’informations sur ces paramètres, consultez la documentation de Google Test.

 ![Paramètres des projets Google Test](media/cpp-gtest-settings.png "Paramètres des projets Google Test")

## <a name="add-include-directives"></a>Ajouter des directives include
Dans votre fichier .cpp de test, ajoutez les directives `#include` nécessaires pour rendre les types et les fonctions de votre programme visibles par le code de test. En règle générale, le programme est un niveau au-dessus dans l’arborescence des dossiers. Si vous tapez `#include "../"`, une fenêtre IntelliSense apparaît et vous permet de sélectionner le chemin complet du fichier d’en-tête.

![Ajouter des directives #include](media/cpp-gtest-includes.png "Ajouter des directives include dans le fichier .cpp de test")

## <a name="write-and-run-tests"></a>Écrire et exécuter des tests
Vous êtes maintenant prêt à écrire et à exécuter des tests Google. Pour plus d’informations sur les macros de test, consultez le [manuel d’introduction à Google Test](https://github.com/google/googletest/blob/master/googletest/docs/Primer.md). Pour plus d’informations sur la découverte, l’exécution et le regroupement de vos tests avec **l’Explorateur de tests**, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](run-unit-tests-with-test-explorer.md).

## <a name="see-also"></a>Voir aussi
[Écriture de tests unitaires pour C/C++](writing-unit-tests-for-c-cpp.md)










