---
title: "Vue d&#39;ensemble du multi-ciblage Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "multi-ciblage (Visual Studio)"
  - "multi-ciblage (Visual Studio)"
  - "cibler la version du .NET Framework (Visual Studio)"
  - "versions (Visual Studio), cibler la version du .NET Framework"
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 36
caps.handback.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Vue d&#39;ensemble du multi-ciblage Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans cette version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vous pouvez spécifier la version de  [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] requise pour votre application.  Par conséquent, si vous souhaitez utiliser cette version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour continuer à développer un projet démarré dans une version antérieure, vous ne devez pas modifier la cible d'infrastructure.  Vous pouvez également créer une solution contenant des projets qui ciblent différentes versions de l'infrastructure.  Le ciblage de framework aide également à garantir que l'application utilise uniquement les fonctionnalités disponibles dans la version spécifiée du framework.  
  
> [!TIP]
>  Vous pouvez également cibler des applications pour différentes plateformes.  Pour plus d’informations, consultez [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)  
  
## Fonctionnalités du ciblage de framework  
 Le ciblage d'infrastructure inclut les fonctionnalités suivantes :  
  
-   Lorsque vous ouvrez un projet qui cible une version antérieure de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] peut automatiquement le mettre à niveau ou laisser la cible telle quelle.  
  
-   Lorsque vous créez un projet, vous pouvez spécifier la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que vous voulez cibler.  
  
-   Vous pouvez modifier la version du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que cible un projet existant.  
  
-   Vous pouvez cibler une version différente du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dans chacun des différents projets de la même solution.  
  
-   Lorsque vous modifiez la version de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ciblée par un projet, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] applique les modifications obligatoires aux références et aux fichiers de configuration.  
  
 Lorsque vous travaillez sur un projet qui cible une version antérieure du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio apporte dynamiquement des modifications dans l'environnement de développement, telles que les suivantes :  
  
-   Il filtre les éléments des boîtes de dialogue **Nouveau projet**, **Ajouter un nouvel élément**, **Ajouter une nouvelle référence** et **Ajouter une référence de service** de façon à omettre les choix qui ne sont pas disponibles dans la version ciblée.  
  
-   Il filtre les contrôles personnalisés de la **Boîte à outils** pour supprimer ceux qui ne sont pas disponibles dans la version ciblée et pour afficher la version la plus récente lorsque plusieurs contrôles sont disponibles.  
  
-   Il filtre IntelliSense en omettant les fonctionnalités de langue qui ne sont pas disponibles dans la version ciblée.  
  
-   Il filtre les propriétés de la fenêtre **Propriétés** de façon à omettre celles qui ne sont pas disponibles dans la version ciblée.  
  
-   Il filtre les options de menu de façon à omettre celles qui ne sont pas disponibles dans la version ciblée.  
  
-   Pour les builds, elle utilise la version du compilateur et les options de compilateur appropriées pour la version ciblée.  
  
> [!NOTE]
>  Le ciblage de framework ne garantit pas que votre application fonctionnera correctement.  Vous devez tester votre application pour vous assurer qu'elle s'exécute sur la version ciblée.  Vous ne pouvez pas cibler des versions .NET Framework antérieures au .NET Framework 2.0.  
  
## Sélection d'une version cible du .NET Framework  
 Lorsque vous créez un projet, sélectionnez la version [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] cible dans la boîte de dialogue **Nouveau projet**.  La liste des modèles de projet disponibles est filtrée selon vos sélections.  Dans un projet existant, vous pouvez modifier la version [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] cible d'un projet dans la boîte de dialogue Propriétés du projet.  Pour plus d'informations, consultez [Comment : cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
> [!NOTE]
>  Dans les éditions Express de Visual Studio, vous ne pouvez pas définir la version cible du .NET Framework dans la boîte de dialogue **Nouveau projet**.  
  
## Résolution des références système et d'assembly utilisateur  
 Pour cibler une version du. Net Framework, vous devez d'abord installer les références d'assembly appropriées.  Les références d'assembly pour les versions 2,0, 3,0, et 3,5 du .Net Framework sont incluses dans le .NET Framework 3.5 SP1, que vous pouvez télécharger à partir du site Web du [Centre de téléchargement Microsoft, Microsoft Visual Studio](http://go.microsoft.com/fwlink/?LinkId=227602) .  Les références d'assembly pour .NET Framework 3.5 Client Profile, le .NET Framework 4, .NET Framework 4 Client Profile, et Silverlight sont également disponibles à la page [Téléchargements Visual Studio](http://go.microsoft.com/fwlink/?LinkId=179687) du site.  
  
> [!NOTE]
>  Un profil client .NET Framework est un sous\-ensemble du .NET Framework qui fournit un jeu limité de bibliothèques et de fonctionnalités.  Pour plus d'informations sur les profils clients, consultez [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
 La boîte de dialogue **Ajouter une référence** désactive les assemblys système qui ne concernent pas la version [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] cible afin qu'ils ne puissent pas être ajoutés à un projet par inadvertance. \(Les assemblys système sont des fichiers .dll qui sont inclus dans une version [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].\) Les références qui appartiennent à une version d'infrastructure qui est ultérieure à la version ciblée ne seront pas résolues, et les contrôles qui dépendent d'une telle référence ne peuvent pas être ajoutés.  Si vous souhaitez activer une telle référence, réinitialisez la cible [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] du projet vers celle qui inclut la référence. Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
 Pour plus d'informations sur les références d'assembly, consultez [Resolving Assemblies at Design Time](../msbuild/resolving-assemblies-at-design-time.md).  
  
## Activation de LINQ  
 Lorsque vous ciblez le .NET Framework 3.5 ou une version ultérieure, une référence à System.Core et un import au niveau du projet pour System.Linq \(Visual Basic uniquement\) sont automatiquement ajoutés.  Si vous voulez utilisez les fonctionnalités LINQ, vous devez également activer Option Infer \(en Visual Basic uniquement\).  La référence et l'importation sont automatiquement supprimées lorsque vous faites passer la version du .Net Framework à une version antérieure.  Pour plus d'informations, consultez [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Voir aussi  
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)   
 [.NET Framework Multi\-Targeting for ASP.NET Web Projects](../Topic/.NET%20Framework%20Multi-Targeting%20for%20ASP.NET%20Web%20Projects.md)   
 [Compatibilité et configurations requises de plateforme](http://www.microsoft.com/visualstudio/eng/products/compatibility)