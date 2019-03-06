---
title: Installer les Versions Visual Studio côte à côte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 67a564b789d24b11b92b218c2a30673c6bd7baad
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54834859"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Installer des versions de Visual Studio côte à côte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio peut être installé sur un ordinateur sur lequel une version antérieure de Visual Studio l’est déjà. Si vous rencontrez un problème d’installation, vous pouvez utiliser l’ [outil de collecte de journaux](http://go.microsoft.com/fwlink/?LinkId=262077) pour collecter des informations sur les échecs de sorte que vous puissiez déboguer les problèmes vous-même.

> [!NOTE]
> Nous vous recommandons d’installer des versions de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dans leur ordre de commercialisation. Par exemple, installez Visual Studio 2013 avant d’installer Visual Studio 2015.

 Avant d’installer plusieurs versions sur la même machine, vérifiez que les conditions suivantes sont bien réunies :

-   Si vous utilisez Visual Studio 2015 pour ouvrir une solution créée dans [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)], vous pouvez par la suite ouvrir et modifier à nouveau la solution dans la version antérieure à condition de ne pas avoir implémenté de fonctionnalités spécifiques à Visual Studio 2015.

-   Si vous essayez d’utiliser Visual Studio 2015 pour ouvrir une solution créée dans [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] ou une version antérieure, vous devrez peut-être modifier vos projets et fichiers pour qu’ils soient compatibles avec Visual Studio 2015. Pour plus d’informations, consultez le [porter, migrer et mettre à niveau des projets Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015) page.

-   Si vous désinstallez une version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sur un ordinateur ayant plusieurs versions installées, les associations de fichiers pour [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sont supprimées pour toutes les versions. Vous pouvez remapper ces associations de fichiers à l’aide du bouton **Restaurer les associations de fichiers** sous les onglets **Environnement**, **Général** de la boîte de dialogue [Options](../ide/reference/general-environment-options-dialog-box.md) .

-   Visual Studio ne met pas automatiquement à niveau les extensions, car elles ne sont pas toutes compatibles. Vous devez réinstaller les extensions à partir de la [Visual Studio Marketplace](http://go.microsoft.com/fwlink/?LinkId=178891) ou l’éditeur de logiciel.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Versions du .NET Framework et installations côte à côte

-   Les projets Visual Basic, Visual C#, Visual F# utilisent l’option **Framework cible** dans le **Concepteur de projets** pour spécifier la version du .NET Framework qu’un projet utilise. Pour un projet C++, vous pouvez changer manuellement la version cible du .NET Framework en modifiant le fichier .vcxproj. Pour plus d’informations, consultez [compatibilité des versions](http://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f).

     Au moment de créer un projet, vous pouvez spécifier la version du .NET Framework que le projet cible dans la liste **.NET Framework** de la boîte de dialogue **Nouveau projet** .

     Pour des informations spécifiques au langage, consultez la rubrique appropriée dans le tableau suivant.

    |Langue|Rubrique|
    |--------------|-----------|
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[Page Application, Concepteur de projets (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|
    |Visual C#|[Page Application, Concepteur de projets (C#)](../ide/reference/application-page-project-designer-csharp.md)|
    |Visual F#|[Configuration de projets](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|
    |C++|[Guide pratique pour modifier le framework cible et l’ensemble d’outils de la plateforme](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[Exécution d’une application JScript sur une version précédente du Common Language Runtime](http://msdn.microsoft.com/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|

## <a name="see-also"></a>Voir aussi

- [Installer Visual Studio](../install/install-visual-studio-2015.md)
- [Porter, migrer et mettre à niveau des projets Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015)
- [Génération d’applications isolées et d’assemblys côte à côte C/C++](http://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)
- [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)