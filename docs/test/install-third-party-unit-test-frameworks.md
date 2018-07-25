---
title: Installer des frameworks de tests unitaires tierces
ms.date: 06/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: d0994b226a80385e381fa7b738c0194ec393d87a
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844691"
---
# <a name="install-third-party-unit-test-frameworks"></a>Installer des frameworks de tests unitaires tierces

L'Explorateur de tests Visual Studio peut exécuter n'importe quel framework de tests unitaires ayant développé une interface d'adaptateur pour l'Explorateur. Le programme d'installation du framework installe les fichiers binaires et ajoute des modèles de projet Visual Studio pour les langages qu'il prend en charge. Lorsque vous créez un projet avec le modèle, le framework est inscrit avec l'Explorateur de tests. Une solution Visual Studio peut contenir des projets de test unitaire qui utilisent des frameworks différents et qui sont destinés à des langages différents. L'Explorateur de tests les exécute tous.

## <a name="acquire-third-party-frameworks"></a>Obtenir des frameworks tiers

Vous pouvez télécharger et installer plusieurs frameworks de test unitaire tiers avec le gestionnaire d’extensions de Visual Studio ou à partir de Visual Studio Marketplace. Il est également possible de télécharger des frameworks à partir d'autres sites tels que le site web du framework.

### <a name="install-from-visual-studio"></a>Installer à partir de Visual Studio

1. Choisissez **Outils** dans le menu standard, puis choisissez **Extensions et mises à jour**.

2. Développez **En ligne** > **Visual Studio Marketplace** > **Outils**. Choisissez **Test**.

3. Parcourez la liste pour rechercher le framework.

4. Sélectionnez le framework, puis choisissez **Télécharger**.

Pour plus d’informations, consultez [Rechercher et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="install-from-the-web"></a>Installation à partir du web

Si vous savez quel framework vous intéresse :

1. Ouvrez [Visual Studio Marketplace ](https://marketplace.visualstudio.com/vs).

2. Tapez le nom du framework dans la zone **Rechercher**.

3. Choisissez le framework dans la liste des résultats pour accéder à la page de Visual Studio Marketplace correspondant à l’outil.

Pour parcourir la liste des frameworks ainsi que d'autres outils de test :

1. Ouvrez [Visual Studio Marketplace ](https://marketplace.visualstudio.com/vs).

2. Dans **Filtrer par catégorie/collection**, choisissez **Tout afficher**.

3. Dans la liste **Catégorie** (libellée **Affichage**), développez le nœud **Outils**, puis choisissez **Test**.

4. Choisissez un framework dans la liste des résultats pour accéder à la page de Visual Studio Marketplace correspondant à l’outil.

## <a name="update-to-the-latest-test-adapters"></a>Mettre à jour vers les adaptateurs de test les plus récents

Mettez à jour vers l’adaptateur de test stable le plus récent afin de bénéficier d’une découverte et d’une exécution de test optimales. Pour plus d’informations sur les mises à jour des adaptateurs de test MSTest, NUnit et xUnit, consultez le [blog de Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/11/16/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Pour mettre à jour vers la version stable la plus récente de l’adaptateur de test

1. Ouvrez le Gestionnaire de package Nuget pour votre solution en accédant à **Outils** > **Gestionnaire de package NuGet** > **Gérer les packages NuGet pour la solution**.

2. Cliquez sur l’onglet **Mises à jour** et recherchez les adaptateurs de test NUnit ou xUnit installés.

3. Sélectionnez chaque adaptateur de test, puis sélectionnez la version stable la plus récente disponible dans le menu déroulant.

4. Choisissez le bouton **Installer**.

   ![Mettre à niveau l’adaptateur de test](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Voir aussi

- [Tests unitaires sur votre code](../test/unit-test-your-code.md)
