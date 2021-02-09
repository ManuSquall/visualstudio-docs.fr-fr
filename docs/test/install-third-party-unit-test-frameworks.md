---
title: Installer des frameworks de tests unitaires tierces
description: L’Explorateur de tests Visual Studio peut exécuter des tests depuis n’importe quel framework de tests unitaires ayant développé une interface d’adaptateur appropriée.
ms.custom: SEO-VS-2020
ms.date: 07/09/2020
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c59a9d9055dd6a5788eec4d4904d9ec41262dae2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879499"
---
# <a name="install-unit-test-frameworks"></a>Installer des frameworks de tests unitaires

L’Explorateur de tests Visual Studio peut exécuter des tests depuis n’importe quel framework de tests unitaires ayant développé une interface d’adaptateur appropriée. L’installation du framework permet de copier les fichiers binaires et d’ajouter des modèles de projet Visual Studio pour les langages pris en charge. Lorsque vous créez un projet avec le modèle, le framework est inscrit avec l'Explorateur de tests.

Une solution Visual Studio peut contenir des projets de test unitaire qui utilisent des frameworks différents et qui sont destinés à des langages différents.

::: moniker range=">=vs-2019"
Pour .NET, [MSTest, nunit et xUnit](getting-started-with-unit-testing.md) sont les frameworks de test fournis par Visual Studio, qui sont installés par défaut. Pour C++, un ensemble différent d’infrastructures de test est fourni, par exemple CTest.
::: moniker-end
::: moniker range="vs-2017"
[MSTest](getting-started-with-unit-testing.md) est le framework de tests fourni par Visual Studio et installé par défaut.
::: moniker-end

## <a name="acquire-frameworks"></a>Acquérir des frameworks

Installez des frameworks de tests unitaires tiers à l’aide du **Gestionnaire de package NuGet**.

1. Cliquez avec le bouton droit sur le projet qui va contenir votre code de test, puis sélectionnez **Gérer les packages NuGet**.

2. Dans le **Gestionnaire de Package NuGet**, recherchez le framework de test à installer, puis cliquez sur **Installer**.

   ![Gestionnaire de package NuGet dans Visual Studio](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>Mettre à jour vers les adaptateurs de test les plus récents

Mettez à jour vers l’adaptateur de test stable le plus récent afin de bénéficier d’une découverte et d’une exécution de test optimales. Pour plus d’informations sur les mises à jour des adaptateurs de test MSTest, NUnit et xUnit, consultez le [blog de Visual Studio](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Pour mettre à jour vers la version stable la plus récente de l’adaptateur de test

1. Ouvrez le gestionnaire de package NuGet pour votre solution en accédant à **Outils**  >  **Gestionnaire de package NuGet**  >  **gérer les packages NuGet pour la solution**.

2. Cliquez sur l’onglet **Mises à jour**, puis recherchez les adaptateurs de test MSTest, NUnit ou xUnit installés.

3. Sélectionnez chaque adaptateur de test, puis sélectionnez la dernière version stable dans le menu déroulant.

4. Choisissez le bouton **Installer**.

   ![Mettre à niveau l’adaptateur de test](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Voir aussi

- [Test unitaire de votre code](../test/unit-test-your-code.md)
