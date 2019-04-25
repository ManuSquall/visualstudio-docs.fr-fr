---
title: Mise à niveau de projets Visual C++ vers Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [C++], upgrading
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 5b0153560173cf8b10ab5e20ebffd47d40baf735
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095741"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Mise à niveau de projets Visual C++ vers Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la documentation la plus récente sur Visual Studio 2017, consultez [Guide du portage et de la mise à niveau de Visual C++](https://docs.microsoft.com/cpp/porting/visual-cpp-porting-and-upgrading-guide).

Lorsque vous ouvrez pour la première fois un projet Visual C++ créé dans une version antérieure de Visual Studio, vous pouvez être invité à le mettre à jour. Le message vous demande si vous souhaitez effectuer une mise à niveau vers la version la plus récente du compilateur et des bibliothèques Visual C++. Les options de mise à niveau dépendent de la version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui a été utilisée pour créer le projet.

 Vous pouvez utiliser [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] pour ouvrir, modifier et générer des projets [!INCLUDE[win8](../includes/win8-md.md)] créés dans [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], mais pour créer un projet [!INCLUDE[win8](../includes/win8-md.md)] , vous devez utiliser [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]. (Pour créer un projet [!INCLUDE[win81](../includes/win81-md.md)] , vous devez utiliser [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].)

 Pour créer un projet Windows 10, vous devez utiliser [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)].

 Si vous n’êtes pas invité à effectuer une mise à jour, vous n’aurez rien à faire pour améliorer le projet.

- Si le projet (.vcproj) a été créé dans une version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] qui est plus ancienne que [!INCLUDE[vs2010](../includes/vs2010-md.md)], vous devez mettre à jour le projet.

- Si le projet (.vcxproj) a été créé dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)],  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]ou [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] , vous disposez de deux options :

    - Vous pouvez ignorer la mise à jour. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] chargera le projet sans effectuer de modification s’il a accès aux outils Visual C++ dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] avec SP1, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] ou [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. Vous pouvez fournir cet accès en installant la version de Visual Studio avec laquelle le projet a été créé sur le même ordinateur doté de [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]. Pour plus d’informations, consultez [Installing Visual Studio Versions Side-by-Side](../install/install-visual-studio-versions-side-by-side.md).

    - Vous pouvez mettre à jour le projet en permettant à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] d’apporter les modifications décrites plus loin dans cette rubrique. Si vous avez plusieurs projets Visual C++ dans votre solution, vous devez tous les mettre à jour.

        > [!NOTE]
        >  Si vous refusez la mise à jour lorsque vous y êtes invité, vous pouvez mettre à jour le projet ultérieurement en ouvrant le menu **Projet** et en choisissant l’option de **mise à jour du projet VC++** . Si la commande ne s’affiche pas, une mise à jour ne sera pas obligatoire.

## <a name="upgrading-a-visual-c-project"></a>Mise à jour d’un projet Visual C++
 Si vous permettez à [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] de mettre automatiquement à jour le projet, ces modifications sont apportées :

- Modifie le projet afin qu’il utilise le compilateur et les bibliothèques [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] (PlatformToolset = VisualStudio v140).

- Pour les projets [!INCLUDE[cppcli](../includes/cppcli-md.md)] , remplace TargetFrameworkVersion par .NET Framework 4.5.2.

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Utilisation constante d’un PlatformToolset personnalisé
 Si vous souhaitez continuer à utiliser un PlatformToolset personnalisé dans [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)], l’ensemble d’outils doit se trouver sous %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ sur un ordinateur x86, ou sous %ProgramFiles (x86)%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ sur un ordinateur x64. Pour plus d’informations sur la création d’un PlatformToolset personnalisé, consultez le billet sur le [multi-ciblage natif C++](http://go.microsoft.com/fwlink/?LinkId=248587) dans le blog de l’équipe Visual C++.

## <a name="see-also"></a>Voir aussi
 [Guide du portage et de la mise à niveau de Visual C++](http://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb) [Portage, migration et mise à niveau des projets Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
