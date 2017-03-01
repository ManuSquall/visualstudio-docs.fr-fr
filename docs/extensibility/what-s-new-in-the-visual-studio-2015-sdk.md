---
title: "Quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2015 | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 8d77fce54b12b90f6a2632fd1c1741990be42a08
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2015
Le Kit de développement logiciel Visual Studio comporte les fonctionnalités nouvelles et mises à jour suivantes pour Visual Studio 2015, mise à jour de Visual Studio 2015 et Visual Studio 2017.  
  
## <a name="vs-2015-sdk-update-1"></a>Mise à jour du SDK Visual Studio 2015 1  
 Mise à jour 1 comprend des outils pour aider votre extension fonctionnent bien avec les thèmes de couleurs et le service d’images Visual Studio.  
  
 Ces rubriques sont sous la [VSSDK utilitaires](../extensibility/internals/vssdk-utilities.md) section :  
  
-   Le [outils de thèmes de couleurs](../extensibility/internals/color-theming-tools.md) vous aider à créer et modifier des couleurs personnalisées pour Visual Studio.  
  
-   Le [Image Service outils](../extensibility/internals/image-service-tools.md) vous permettent d’utiliser avec des fichiers manifeste image de Visual Studio.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nouvelle façon d’ajouter le Kit de développement logiciel de Visual Studio dans Visual Studio  
 À partir de Visual Studio 2015, vous n’avez pas besoin de télécharger le Kit de développement logiciel Visual Studio séparément. En revanche, vous pouvez l’installer dans le cadre du processus d’installation normal, ou vous pouvez choisir de l’installer ultérieurement sur. Lorsque vous ouvrez ou créez une solution VSIX, Visual Studio vous demandera d’installer les outils d’extensibilité de Visual Studio. Pour plus d’informations, consultez [l’installation du Kit de développement logiciel Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Nouvelles façons de créer des Extensions  
 À partir du Kit de développement logiciel Visual Studio 2015, vous disposez des options différentes pour créer des extensions, selon le langage de programmation que vous utilisez.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# et Visual Basic  
 Pour c# et Visual Basic, il existe un ensemble de modèles d’élément de projet qui vous permettent de créer des packages VS, commandes de menu, fenêtres Outil, éditeur classifieurs, ornements d’éditeur et extensions marge de l’éditeur. Vous pouvez ajouter tout ou partie de ces options pour le projet VSIX standard. Pour plus d'informations, voir :  
  
-   [Création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Création d’une Extension avec un éditeur de modèle d’élément](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Création d’une Extension avec un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     L’Assistant VSPackage ne crée plus extensions en c# ou Visual Basic.  
  
### <a name="c"></a>C++  
 Pour C++, l’Assistant VSPackage prend en charge les commandes de menu, les fenêtres Outil et les éditeurs personnalisés. Recherchez dans le **nouveau projet** boîte de dialogue de **Visual C++ / extensibilité**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Assemblys de référence SDK de Visual Studio via NuGet  
 Pour améliorer la portabilité et le partage de projets d’extensibilité, vous pouvez utiliser les versions NuGet des assemblys de référence du Kit de développement logiciel Visual Studio.  Ils sont disponibles sur [nuget.org](http://www.nuget.org) publié par [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) et peut être facilement ajouté à votre projet ou solution via Visual Studio **fait référence à / gérer les Packages NuGet** boîte de dialogue. Vous pouvez ajouter des références aux assemblys d’extensibilité spécifiques ou ajouter le SDK de Visual Studio fait référence à des assemblys à la fois à l’aide du Kit de développement logiciel Visual Studio [package de métadonnées](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Pour plus d’informations sur NuGet, consultez [vue d’ensemble de NuGet](http://docs.nuget.org/) et [gérer NuGet Packages à l’aide de la boîte de dialogue](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
 Lorsque vous utilisez les versions NuGet des assemblys de référence du Kit de développement logiciel Visual Studio, un autre utilisateur n’a pas besoin d’installer le Kit de développement Visual Studio pour ouvrir et générer votre projet.  Les assemblys de référence NuGet et outils de génération Visual Studio SDK seront automatiquement installés sur leur ordinateur pour ce projet.  
  
 Les modèles d’élément Visual Studio SDK utilisent NuGet pour leurs références et outils de génération et vous offre les avantages de NuGet par défaut.  
  
> [!NOTE]
>  Vous pouvez continuer à utiliser des assemblys de référence du Kit de développement logiciel Visual Studio installée avec vos projets (situé sous \<emplacement d’installation Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) et les projets d’extensibilité existants n’avez pas besoin d’être mis à niveau pour utiliser les packages NuGet.  Le projet **fait référence à / ajouter la référence** boîte de dialogue continue d’utiliser des assemblys de référence du Kit de développement logiciel Visual Studio installé.  
>   
>  Si vous souhaitez modifier vos projets existants pour utiliser NuGet, consultez [Comment : migrer les packages VS pour Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) qui comporte une section sur la mise à jour des projets d’extensibilité pour les packages NuGet.  
  
## <a name="light-bulbs"></a>Les ampoules  
 Un des plus nouvelles méthodes d’écriture de code d’extension est fourni par le projet Roslyn. Pour plus d’informations, consultez [Roslyn](https://github.com/dotnet/Roslyn).  
  
 Les ampoules sont une nouvelle fonctionnalité qui est livré avec VSSDK. Il s’agit d’icônes utilisées dans l’éditeur Visual Studio qui se développent pour afficher un ensemble d’actions de refactorisation de code ou des correctifs pour les problèmes identifiés par les analyseurs de code intégré. Pour plus d’informations, consultez [procédure pas à pas : affichage des Suggestions ampoule](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Consignes d’environnement utilisateur mis à jour  
 Conception de nouvelles extensions ou fonctionnalités de Visual Studio ? Découvrez les mises à jour et étendu [recommandations pour l’environnement utilisateur Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Vous trouverez le [couleur jetons](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [les tailles de police](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [spécifications de mise en page de boîte de dialogue](../extensibility/ux-guidelines/layout-for-visual-studio.md)et autres conseils nécessaires pour intégrer sans difficulté votre nouvelle interface utilisateur avec Visual Studio.
