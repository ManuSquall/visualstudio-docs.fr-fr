---
title: Quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2015 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c419800a92f25ce4531c351d4131acf119633ccb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949228"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Ce que&#39;s dans le Kit de développement logiciel Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le SDK Visual Studio a les fonctionnalités nouvelles et mises à jour suivantes pour Visual Studio 2015, Visual Studio 2015 mise à jour et Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

À partir de Visual Studio 2017, l’analyse pour les modèles de projets et modèles d’élément est n’est plus effectuée. Au lieu de cela, l’extension doit fournir les fichiers de manifeste de modèle qui décrivent l’emplacement d’installation de ces modèles. Vous pouvez utiliser Visual Studio 2017 pour mettre à jour vos extensions VSIX. Si vous déployez votre extension à l’aide d’un fichier MSI, vous devez générer manuellement les fichiers manifeste de modèle. Pour plus d’informations, consultez [Upgrading Custom Project et des modèles d’élément pour Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Le schéma de manifeste de modèle est documenté dans [référence modèle Visual Studio Manifest schéma](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>Visual Studio 2015 SDK Update 1
 Mise à jour 1 inclut des outils pour aider à votre extension fonctionnent correctement avec les thèmes de couleurs et le service d’images Visual Studio.

 Ces rubriques sont sous la [utilitaires VSSDK](../extensibility/internals/vssdk-utilities.md) section :

-   Le [outils de thèmes de couleur](../extensibility/internals/color-theming-tools.md) vous aider à créer et modifier des couleurs personnalisées pour Visual Studio.

-   Le [Image Service outils](../extensibility/internals/image-service-tools.md) vous permettent d’utiliser avec des fichiers manifeste image de Visual Studio.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nouvelle façon d’ajouter le SDK Visual Studio dans Visual Studio
 À partir de Visual Studio 2015, vous n’avez pas besoin de télécharger le SDK Visual Studio séparément. Au lieu de cela, vous pouvez l’installer dans le cadre du processus d’installation normale, ou vous pouvez choisir de l’installer ultérieurement sur. Lorsque vous ouvrez ou créez une solution VSIX, Visual Studio vous demandera d’installer les outils d’extensibilité de Visual Studio. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Nouvelles méthodes de création d’Extensions
 À partir du Kit de développement logiciel Visual Studio 2015, vous disposez des options différentes pour créer des extensions, en fonction de langage de programmation que vous utilisez.

### <a name="visual-c-and-visual-basic"></a>Visual C# et Visual Basic
 Pour c# et Visual Basic, il existe une gamme complète de modèles d’élément de projet qui vous permettent de créer des VSPackages, commandes de menu, fenêtres Outil, éditeur classifieurs, ornements d’éditeur et extensions marge de l’éditeur. Vous pouvez ajouter tout ou partie de ces options pour le projet VSIX standard. Pour plus d'informations, voir :

-   [Création d’une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

-   [Création d’une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md)

-   [Création d’une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md)

-   [Création d’une extension avec un package VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     L’Assistant package Visual Studio ne crée plus extensions en c# ou Visual Basic.

### <a name="c"></a>C++
 Pour C++, l’Assistant package Visual Studio prend en charge les commandes de menu, les fenêtres Outil et les éditeurs personnalisés. Recherchez dans le **nouveau projet** boîte de dialogue de **Visual C++ / extensibilité**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Assemblys de référence SDK de Visual Studio via NuGet
 Pour améliorer la portabilité et le partage des projets d’extensibilité, vous pouvez utiliser les versions NuGet des assemblys de référence du Kit de développement logiciel Visual Studio.  Ils sont disponibles sur [nuget.org](http://www.nuget.org) publié par [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) et peut être facilement ajouté à votre projet ou solution à l’aide Visual Studio **fait référence à / gérer NuGet Packages** boîte de dialogue. Vous pouvez ajouter des références aux assemblys d’extensibilité spécifique au individuelles ou ajouter des assemblys à la fois à l’aide du SDK de Visual Studio fait référence à tous les SDK de Visual Studio [méta package](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Pour en savoir plus sur NuGet, consultez [vue d’ensemble de NuGet](http://docs.nuget.org/) et [gérer NuGet Packages à l’aide de la boîte de dialogue](http://docs.nuget.org/Consume/Package-Manager-Dialog).

 Lorsque vous utilisez les versions NuGet des assemblys de référence du Kit de développement logiciel Visual Studio, un autre utilisateur n’a pas besoin d’installer le Kit de développement Visual Studio pour ouvrir et générer votre projet.  Les assemblys de référence de NuGet et les outils de génération de SDK de Visual Studio seront automatiquement être installés sur leur ordinateur pour ce projet.

 Les modèles d’élément Visual Studio SDK utilisent NuGet pour leurs références et outils de génération et vous offre les avantages de NuGet par défaut.

> [!NOTE]
>  Vous pouvez continuer à utiliser les assemblys de référence du Kit de développement logiciel Visual Studio installé avec vos projets (situé sous \<emplacement d’installation Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) et les projets d’extensibilité existants n’êtes pas obligé d’être mise à niveau pour utiliser les packages NuGet.  Le projet **fait référence à / ajouter une référence** dialogue continue d’utiliser les assemblys de référence du Kit de développement logiciel Visual Studio installé.
>
>  Si vous souhaitez modifier vos projets existants pour utiliser NuGet, consultez [Comment : Migrer les packages VS pour Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) qui comporte une section sur la mise à jour de projets d’extensibilité pour les packages NuGet.

## <a name="light-bulbs"></a>Les ampoules
 Une des plus nouvelles méthodes d’écriture de code d’extension est fournie par le projet Roslyn. Pour plus d’informations, consultez [Roslyn](https://github.com/dotnet/Roslyn).

 Les ampoules sont une nouvelle fonctionnalité qui est fourni avec l’extensibilité Visual Studio. Ils sont les icônes utilisées dans l’éditeur Visual Studio et qui se développent pour afficher un ensemble d’actions de refactorisation de code ou de correctifs pour les problèmes identifiés par les analyseurs de code intégré. Pour plus d’informations, consultez [Procédure pas à pas : Displaying Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Recommandations pour l’expérience utilisateur mis à jour
 Conception de nouvelles extensions ou des fonctionnalités pour Visual Studio ? Découvrez les mises à jour et développé [recommandations pour l’expérience utilisateur Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Vous trouverez le [jetons de couleur](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [les tailles de police](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [spécifications de mise en page de boîte de dialogue](../extensibility/ux-guidelines/layout-for-visual-studio.md)et d’autres instructions, vous devez intégrer en toute transparence votre nouvelle interface utilisateur avec Visual Studio.
