---
title: Nouveautés du kit de développement logiciel (SDK) Visual Studio 2015 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d47e40a5c38eeb7898aa179282fa55bbe17ef1d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917328"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>&#39;nouveautés du kit de développement logiciel (SDK) Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le kit de développement logiciel (SDK) Visual Studio propose les fonctionnalités nouvelles et mises à jour suivantes pour Visual Studio 2015, Visual Studio 2015 mis à jour et Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

À compter de Visual Studio 2017, l’analyse des modèles de projet et d’élément personnalisés ne sera plus effectuée. Au lieu de cela, l’extension doit fournir des fichiers manifestes de modèle qui décrivent l’emplacement d’installation de ces modèles. Vous pouvez utiliser Visual Studio 2017 pour mettre à jour vos extensions VSIX. Si vous déployez votre extension à l’aide d’un MSI, vous devez générer manuellement les fichiers manifeste de modèle. Pour plus d’informations, consultez [mise à niveau d’un modèles de projet et d’élément pour Visual Studio personnalisé 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Le schéma de manifeste de modèle est documenté dans [référence de schéma du manifeste de modèle Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>SDK VS 2015 Update 1
 Update 1 comprend des outils pour aider votre extension à fonctionner correctement avec les thèmes de couleur et le service d’images Visual Studio.

 Ces rubriques se trouvent sous la section [utilitaires VSSDK](../extensibility/internals/vssdk-utilities.md) :

- Les [outils de coloration des couleurs](../extensibility/internals/color-theming-tools.md) vous aident à créer et à modifier des couleurs personnalisées pour Visual Studio.

- Les [outils de service d’image](../extensibility/internals/image-service-tools.md) vous permettent d’utiliser des fichiers manifeste d’image Visual Studio.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nouvelle méthode pour ajouter le kit de développement logiciel (SDK) Visual Studio à Visual Studio
 À compter de Visual Studio 2015, vous n’avez pas besoin de télécharger le kit de développement logiciel (SDK) Visual Studio séparément. Au lieu de cela, vous pouvez l’installer dans le cadre du processus d’installation normal, ou vous pouvez choisir de l’installer ultérieurement. Quand vous ouvrez ou créez une solution VSIX, Visual Studio vous demande d’installer le Outils d’extensibilité de Visual Studio. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Nouvelles façons de créer des extensions
 À partir du kit de développement logiciel (SDK) Visual Studio 2015, vous disposez de différentes options pour créer des extensions, en fonction du langage de programmation que vous utilisez.

### <a name="visual-c-and-visual-basic"></a>Visual C# et Visual Basic
 Pour C# et Visual Basic, il existe une gamme complète de modèles d’élément de projet qui vous permettent de créer des VSPackages, des commandes de menu, des fenêtres outil, des classifieurs de l’éditeur, des ornements de l’éditeur et des extensions de marge de l’éditeur. Vous pouvez ajouter tout ou partie de ces derniers au projet VSIX standard. Pour plus d'informations, consultez les pages suivantes :

- [Création d’une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Création d’une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Création d’une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [Création d’une extension avec un package VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     L’Assistant VSPackage ne crée plus d’extensions en C# ou en Visual Basic.

### <a name="c"></a>C++
 Pour C++, l’Assistant VSPackage prend en charge les commandes de menu, les fenêtres outil et les éditeurs personnalisés. Recherchez-le dans la boîte de dialogue **nouveau projet** dans **Visual C++/extensibilité**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Assemblys de référence du kit de développement logiciel VS SDK via NuGet
 Pour une portabilité et un partage des projets d’extensibilité accrus, vous pouvez utiliser les versions NuGet des assemblys de référence du kit de développement logiciel (SDK) VS.  Celles-ci sont disponibles sur [NuGet.org](https://www.nuget.org/) publié par [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) et peuvent être facilement ajoutées à votre projet ou votre solution par le biais de la boîte de dialogue **références/gestion des packages NuGet** de Visual Studio. Vous pouvez ajouter des références individuelles à des assemblys d’extensibilité spécifiques ou ajouter tous les assemblys de référence du kit de développement logiciel (SDK) Visual Studio à la fois à l’aide du [package méta](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)SDK vs. Pour en savoir plus sur NuGet, consultez [vue d’ensemble de NuGet](/nuget/) et [gérer les packages NuGet à l’aide de la boîte de dialogue](/nuget/consume-packages/install-use-packages-visual-studio).

 Quand vous utilisez les versions NuGet des assemblys de référence du kit de développement logiciel (SDK) VS, un autre utilisateur n’a pas besoin d’installer le kit de développement logiciel (SDK) Visual Studio pour ouvrir et générer votre projet.  Les assemblys de référence NuGet et les outils de génération du kit de développement logiciel VS SDK seront automatiquement installés sur leur ordinateur pour ce projet.

 Les modèles d’élément du kit de développement logiciel (SDK) VS utilisent NuGet pour leurs références et outils de génération, ce qui vous permet d’obtenir les avantages de NuGet par défaut.

> [!NOTE]
> Vous pouvez continuer à utiliser les assemblys de référence installés avec Visual Studio SDK avec vos projets (situés sous \<Visual Studio Install Location> \ VSSDK\VisualStudioIntegration\Common\Assemblies) et les projets d’extensibilité existants n’ont pas besoin d’être mis à niveau pour utiliser des packages NuGet.  La boîte de dialogue références de projet **/Ajouter une référence** continue à utiliser les assemblys de référence SDK Visual Studio.
>
> Si vous souhaitez modifier vos projets existants pour utiliser NuGet, consultez Guide pratique [pour migrer les VSPackages vers Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) qui contient une section sur la mise à jour des projets d’extensibilité vers des packages NuGet.

## <a name="light-bulbs"></a>Ampoules
 L’un des nouveaux moyens les plus passionnants d’écrire du code d’extension est fourni par le projet Roslyn. Pour plus d’informations, consultez [Roslyn](https://github.com/dotnet/Roslyn).

 Les ampoules sont une nouvelle fonctionnalité qui est fournie avec le VSSDK. Il s’agit d’icônes utilisées dans l’éditeur Visual Studio qui se développent pour afficher un ensemble d’actions ou de correctifs de refactorisation du code pour les problèmes identifiés par les analyseurs de code intégrés. Pour plus d’informations, consultez [procédure pas à pas : affichage des suggestions d’ampoules](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Instructions d’expérience utilisateur mises à jour
 Vous concevez de nouvelles extensions ou fonctionnalités pour Visual Studio ? Consultez les instructions de l' [expérience utilisateur Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)mise à jour et développée.  Vous trouverez les [jetons de couleur](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), les [tailles de police](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), les spécifications de [mise en page de boîte de dialogue](../extensibility/ux-guidelines/layout-for-visual-studio.md)et d’autres conseils dont vous avez besoin pour intégrer votre nouvelle interface utilisateur en toute transparence à Visual Studio.
