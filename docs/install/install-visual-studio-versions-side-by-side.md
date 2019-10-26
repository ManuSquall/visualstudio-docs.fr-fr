---
title: Installer des versions de Visual Studio côte à côte
ms.date: 03/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b7fb1e057ffd9f3824fa1fe49e353fd54694da91
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888684"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Installer des versions de Visual Studio côte à côte

Vous pouvez installer Visual Studio sur un ordinateur sur lequel une version antérieure ou ultérieure de Visual Studio est déjà installée.

::: moniker range="vs-2017"

Avant d’installer plusieurs versions sur la même machine, vérifiez que les conditions suivantes sont bien réunies :

* Si vous utilisez Visual Studio 2017 pour ouvrir une solution créée dans Visual Studio 2015, vous pouvez par la suite ouvrir et modifier à nouveau la solution dans la version antérieure à condition de ne pas avoir implémenté de fonctionnalités spécifiques à Visual Studio 2017.

* Si vous essayez d’utiliser Visual Studio 2017 pour ouvrir une solution créée dans Visual Studio 2015 ou une version antérieure, vous devrez peut-être modifier vos projets et fichiers pour qu’ils soient compatibles avec Visual Studio 2017. Pour plus d’informations, consultez la page [Porter, migrer et mettre à niveau des projets Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017).

::: moniker-end

::: moniker range=">= vs-2019"

Avant d’installer plusieurs versions sur la même machine, vérifiez que les conditions suivantes sont bien réunies :

* Si vous utilisez Visual Studio 2019 pour ouvrir une solution créée dans Visual Studio 2017, vous pouvez par la suite ouvrir et modifier à nouveau la solution dans la version antérieure à condition de ne pas avoir implémenté de fonctionnalités spécifiques à Visual Studio 2019.

* Si vous essayez d’utiliser Visual Studio 2019 pour ouvrir une solution créée dans Visual Studio 2017 ou une version antérieure, vous devrez peut-être modifier vos projets et fichiers pour qu’ils soient compatibles avec Visual Studio 2019. Pour plus d’informations, consultez la page [Porter, migrer et mettre à niveau des projets Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

::: moniker-end

* Si vous désinstallez une version de Visual Studio sur un ordinateur ayant plusieurs versions installées, les associations de fichiers pour Visual Studio sont supprimées pour toutes les versions.

* Visual Studio ne met pas automatiquement à niveau les extensions, car elles ne sont pas toutes compatibles. Vous devez réinstaller les extensions à partir de [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou de l’éditeur du logiciel.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Versions du .NET Framework et installations côte à côte

Les projets Visual Basic, Visual C# et Visual F# utilisent l’option **Framework cible** dans le **Concepteur de projets** pour spécifier la version du .NET Framework qu’un projet utilise. Pour un projet C++, vous pouvez changer manuellement la version cible du .NET Framework en modifiant le fichier .vcxproj. Pour plus d’informations, consultez la page [Compatibilité de versions dans le .NET Framework](/dotnet/framework/migration-guide/version-compatibility).

Au moment de créer un projet, vous pouvez spécifier la version du .NET Framework que le projet cible dans la liste **.NET Framework** de la boîte de dialogue **Nouveau projet** .

Pour des informations spécifiques au langage, consultez la rubrique appropriée dans le tableau suivant.

::: moniker range="vs-2017"

| Langue | Rubrique |
|--------------|-----------|
| Visual Basic | [Page Application, Concepteur de projet (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Page Application, Concepteur de projets (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Développer avec Visual F# dans Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Comment : modifier le Framework cible et l’ensemble d’outils de plateforme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md?view=vs-2017)
* [Porter, migrer et mettre à niveau des projets Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [Génération d’applications isolées et d’assemblys côte à côte C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Langue | Rubrique |
|--------------|-----------|
| Visual Basic | [Page Application, Concepteur de projet (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Page Application, Concepteur de projets (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Développer avec Visual F# dans Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [Comment : modifier le Framework cible et l’ensemble d’outils de plateforme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Porter, migrer et mettre à niveau des projets Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Génération d’applications isolées et d’assemblys côte à côte C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end