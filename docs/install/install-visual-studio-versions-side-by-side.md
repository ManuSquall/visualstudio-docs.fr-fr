---
title: Installer des versions de Visual Studio côte à côte
ms.date: 07/24/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.openlocfilehash: b0e5a2d09cad35266bacc73580b2284f66bd32f5
ms.sourcegitcommit: d97d72308ef306e7f28c3a76913caee4ff450bbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90713462"
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

## <a name="install-minor-visual-studio-versions-side-by-side"></a>Installer côte à côte des versions mineures de Visual Studio

Lors de la mise à niveau d’une version mineure de Visual Studio vers la suivante, le programme d’installation de Visual Studio met à jour votre installation actuelle vers la version suivante de ce canal par défaut. Par exemple, lors de l’installation de la version préliminaire de 16.6.4, le programme d’installation tente de remplacer votre installation actuelle de 16.6.3 Preview, car les deux versions se trouvent dans le canal 16,6 Preview. Cela permet de s’assurer que les versions antérieures de Visual Studio n’occupent pas de place sur votre ordinateur. Dans certains cas spécifiques, il peut être utile d’installer les versions mineures côte à côte. Dans notre exemple, cela signifie que 16.6.3 et 16.6.4 se trouvent tous deux sur le même ordinateur.

1. Téléchargez le [fichier du programme d’amorçage de Visual Studio](/visualstudio/releases/2019/history#installing-an-earlier-release) pour la version mineure que vous souhaitez installer côte à côte avec vos versions existantes de Visual Studio.
2. Ouvrez l’invite de commandes en mode administrateur. Pour ce faire, ouvrez le menu Démarrer de Windows, tapez « cmd », cliquez avec le bouton droit sur le résultat de la recherche de l’invite de commandes, puis sélectionnez **exécuter en tant qu’administrateur**. Dans l’invite de commandes, remplacez le répertoire par le dossier où se trouve votre fichier de programme d’amorçage de Visual Studio.
3. Exécutez la commande ci-dessous, en spécifiant un nouveau chemin d’accès au dossier pour l’emplacement d’installation et en remplaçant le nom du fichier. exe par le nom du programme d’amorçage approprié pour la version de Visual Studio que vous installez. Le nom du fichier. exe doit correspondre à l’un des fichiers suivants :
   * vs_community.exe pour Visual Studio Community
   * vs_professional.exe pour Visual Studio Professional
   * vs_enterprise.exe pour Visual Studio Enterprise

   ```
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<2019 AddNewPath>"
   ```

4. Suivez les boîtes de dialogue du programme d’installation pour sélectionner les composants dont vous avez besoin pour votre installation. Pour plus d’informations, consultez [installer Visual Studio](install-visual-studio.md#step-4---choose-workloads).

## <a name="net-framework-versions-and-side-by-side-installations"></a>Versions du .NET Framework et installations côte à côte

Les projets Visual Basic, Visual C# et Visual F# utilisent l’option **Framework cible** dans le **Concepteur de projets** pour spécifier la version du .NET Framework qu’un projet utilise. Pour un projet C++, vous pouvez changer manuellement la version cible du .NET Framework en modifiant le fichier .vcxproj. Pour plus d’informations, consultez la page [Compatibilité de versions dans le .NET Framework](/dotnet/framework/migration-guide/version-compatibility).

Au moment de créer un projet, vous pouvez spécifier la version du .NET Framework que le projet cible dans la liste **.NET Framework** de la boîte de dialogue **Nouveau projet** .

Pour des informations spécifiques au langage, consultez la rubrique appropriée dans le tableau suivant.

::: moniker range="vs-2017"

| Langage | Rubrique |
|--------------|-----------|
| Visual Basic | [Page Application, Concepteur de projet (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Page Application, Concepteur de projet (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Développer avec Visual F# dans Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Procédure : modifier le framework cible et l’ensemble d’outils de plateforme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md?view=vs-2017)
* [Porter, migrer et mettre à niveau des projets Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [Génération d’applications isolées et d’assemblys côte à côte C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Langage | Rubrique |
|--------------|-----------|
| Visual Basic | [Page Application, Concepteur de projet (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Page Application, Concepteur de projet (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Développer avec Visual F# dans Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [Procédure : modifier le framework cible et l’ensemble d’outils de plateforme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Voir aussi

* [Installer Visual Studio](install-visual-studio.md)
* [Porter, migrer et mettre à niveau des projets Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Génération d’applications isolées et d’assemblys côte à côte C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end