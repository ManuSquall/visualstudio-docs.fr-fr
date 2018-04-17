---
title: Ce que&#39;nouveauté dans le Kit de développement logiciel Visual Studio 2015 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6488f28f2963e17c716c2e9d395ddf77f270e7b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Ce que&#39;nouveauté dans le Kit de développement logiciel Visual Studio 2015
Le Kit de développement logiciel Visual Studio a les fonctionnalités nouvelles et mises à jour suivantes pour Visual Studio 2015, Visual Studio 2015 mise à jour et Visual Studio 2017.  
  
## <a name="vs-2015-sdk-update-1"></a>Visual Studio 2015 SDK Update 1  
 Mise à jour 1 inclut des outils pour aider votre extension fonctionnent correctement avec les thèmes de couleurs et le service d’images Visual Studio.  
  
 Ces rubriques sont sous la [utilitaires d’extensibilité Visual Studio](../extensibility/internals/vssdk-utilities.md) section :  
  
-   Le [outils de thèmes de couleurs](../extensibility/internals/color-theming-tools.md) vous aider à créer et modifier des couleurs personnalisées pour Visual Studio.  
  
-   Le [outils d’Image de Service](../extensibility/internals/image-service-tools.md) permettent de travailler avec des fichiers manifestes de Visual Studio image.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nouvelle façon d’ajouter le SDK de Visual Studio à Visual Studio  
 À partir de Visual Studio 2015, vous n’avez pas besoin de télécharger le Kit de développement logiciel Visual Studio séparément. Au lieu de cela, vous pouvez l’installer dans le cadre du processus d’installation normale, ou vous pouvez choisir d’installer plus tard. Lorsque vous ouvrez ou créez une solution VSIX, Visual Studio vous demandera d’installer les outils d’extensibilité de Visual Studio. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Nouvelles façons de créer des Extensions  
 À partir du Kit de développement logiciel Visual Studio 2015, vous disposez des options différentes pour créer des extensions, selon le langage de programmation que vous utilisez.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# et Visual Basic  
 Pour c# et Visual Basic, il est un ensemble de modèles d’élément de projet qui vous permettent de créer des VSPackages, commandes de menu, les fenêtres Outil, éditeur classifieurs, ornements d’éditeur et extensions marge de l’éditeur. Vous pouvez ajouter tout ou partie de ces options pour le projet VSIX standard. Pour plus d'informations, voir :  
  
-   [Création d’une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Création d’une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Création d’une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Création d’une extension avec un package VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     L’Assistant VSPackage ne crée plus extensions en c# ou Visual Basic.  
  
### <a name="c"></a>C++  
 Pour C++, l’Assistant VSPackage prend en charge les commandes de menu, les fenêtres Outil et les éditeurs personnalisés. Recherchez dans le **nouveau projet** boîte de dialogue de **Visual C++ / extensibilité**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Assemblys de référence de kit de développement logiciel Visual Studio via NuGet  
 Pour une meilleure portabilité et le partage de projets d’extensibilité, vous pouvez utiliser les versions de NuGet des assemblys de référence du Kit de développement logiciel Visual Studio.  Ils sont disponibles sur [nuget.org](http://www.nuget.org) publié par [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) et peuvent être facilement ajoutés à votre projet ou solution via Visual Studio **fait référence à / gérer NuGet Packages** boîte de dialogue. Vous pouvez ajouter des références aux assemblys d’extensibilité spécifique ou tous le Kit de développement Visual Studio fait référence à des assemblys à la fois à l’aide du Kit de développement logiciel Visual Studio [package de métadonnées](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Pour plus d’informations sur NuGet, consultez le [documentation de NuGet](/NuGet) et [Package Manager UI](/NuGet/Tools/Package-Manager-UI) rubriques.  
  
 Lorsque vous utilisez les versions de NuGet des assemblys de référence du Kit de développement logiciel Visual Studio, un autre utilisateur n’a pas besoin d’installer le Kit de développement Visual Studio pour ouvrir et générer votre projet.  Les assemblys de référence de NuGet et outils de génération Visual Studio SDK installe automatiquement sur leur ordinateur pour ce projet.  
  
 Les modèles d’élément Visual Studio SDK utilisent NuGet pour leurs références et les outils de génération et vous offre les avantages de NuGet par défaut.  
  
> [!NOTE]
>  Vous pouvez continuer à utiliser des assemblys de référence du Kit de développement logiciel Visual Studio installé avec vos projets (situé sous \<emplacement d’installation Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) et les projets d’extensibilité existants n’avez pas besoin d’être mise à niveau pour utiliser les packages NuGet.  Le projet **fait référence à / ajouter une référence** boîte de dialogue continue d’utiliser des assemblys de référence du Kit de développement logiciel Visual Studio installé.  
>   
>  Si vous souhaitez modifier vos projets existants pour utiliser NuGet, consultez [Comment : migrer les VSPackages Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) qui comporte une section sur la mise à jour des projets d’extensibilité dans les packages NuGet.  
  
## <a name="light-bulbs"></a>Les ampoules  
 Un des plus nouvelles méthodes d’écriture de code de l’extension est fourni par le projet Roslyn. Pour plus d’informations, consultez [Roslyn](https://github.com/dotnet/Roslyn).  
  
 Les ampoules sont une nouvelle fonctionnalité qui est fourni avec l’extensibilité Visual Studio. Il s’agit des icônes utilisées dans l’éditeur Visual Studio et qui se développent pour afficher un ensemble d’actions de refactorisation de code ou des correctifs pour les problèmes identifiés par les analyseurs de code intégré. Pour plus d’informations, consultez [procédure pas à pas : affichage des Suggestions ampoule](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Recommandations pour l’expérience utilisateur mis à jour  
 Conception de nouvelles extensions ou des fonctionnalités de Visual Studio ? Vérifier la mise à jour et l’étendue [recommandations expérience utilisateur de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Vous trouverez le [jetons de couleur](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [tailles de police](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [spécifications de mise en page de boîte de dialogue](../extensibility/ux-guidelines/layout-for-visual-studio.md)et d’autres conseils nécessaires pour intégrer en toute transparence votre nouvelle interface utilisateur de Visual Studio.