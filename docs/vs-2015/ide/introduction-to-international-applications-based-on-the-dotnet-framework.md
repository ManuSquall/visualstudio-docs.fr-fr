---
title: Introduction aux applications internationales basées sur le .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- strings [Visual Studio], localizing
- Web applications [.NET Framework], globalization
- Windows Forms, globalization
- localization [Visual Studio], culture setting
- fallback resources
- culture, setting
- globalization [Visual Studio], culture setting
- resources [Visual Studio], localization
- localization [Visual Studio], .NET localization model
- Assembly Resource file template
- resources [Visual Studio], fallback system
- international applications [Visual Studio], about international applications
- globalization [Visual Studio], international applications
- ASP.NET, globalization
- resource files, fallback processes
- user interface, culture setting
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0d57cee8591196d12e51e58fb0e5e6a4a2cdf94a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75848375"
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>Introduction aux applications internationales basées sur le .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], il existe deux parties pour la création d’une application mondialisable : la globalisation (processus de conception d’applications pouvant s’adapter à différentes cultures) et la localisation (processus de traduction de ressources pour une culture spécifique). Pour des informations générales sur la conception d’applications à destination d’un public international, consultez [Bonnes pratiques pour développer des applications mondialisables](https://msdn.microsoft.com/library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c).

 Le modèle de localisation [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] se compose d’un assembly principal qui contient le code d’application et les ressources de secours : chaînes, images et autres objets pour le langage dans lequel l’application a été initialement développée. Chaque application localisée dispose d’assemblys satellites (assemblys qui contiennent uniquement les ressources localisées). Étant donné que l’assembly principal contient toujours les ressources de secours, si une ressource est introuvable dans l’assembly satellite localisé, le <xref:System.Resources.ResourceManager> tente de la charger de façon hiérarchique, en recourant en dernier ressort à la ressource dans l’assembly principal. Le système de secours de ressources est expliqué en détail dans [Organisation hiérarchique des ressources pour la localisation](../ide/hierarchical-organization-of-resources-for-localization.md).

 Une ressource de localisation que nous vous encourageons à utiliser est le glossaire pour tous les produits Microsoft localisés. Ce fichier CSV contient plus de 12 000 termes anglais, ainsi que les traductions des termes dans 59 langues différentes. Le glossaire est disponible en téléchargement sur la page web [Microsoft Terminology Translations](https://msdn.microsoft.com/goglobal/bb688105.aspx) (Traductions terminologiques Microsoft).

 Le système de projet pour les applications Windows Forms peut générer des fichiers de ressources pour la culture de secours et chaque culture d’interface utilisateur supplémentaire souhaitée. Le fichier de ressources de secours est intégré à l’assembly principal, puis les fichiers de ressources spécifiques à une culture sont intégrés aux assemblys satellites, à raison d’un par culture d’interface utilisateur. Quand vous générez un projet, les fichiers de ressources sont compilés à partir du format XML de Visual Studio (.resx) dans un format binaire intermédiaire (.resources), puis incorporés dans des assemblys satellites.

 Le système de projet pour les Windows Forms et Web Forms vous permet de générer des fichiers de ressources à l’aide d’un modèle de fichier de ressources d’assembly, d’accéder aux ressources et de générer votre projet. Les assemblys satellites sont créés avec l’assembly principal.

 Quand une application localisée s’exécute, deux valeurs de culture déterminent son apparence. (Une *culture* est un ensemble d’informations de préférences utilisateur relatives à la langue, à l’environnement et aux conventions culturelles de l’utilisateur.) Le paramètre de culture d’interface utilisateur détermine les ressources qui seront chargées. La culture de l’interface utilisateur est définie en tant que `UICulture` dans les fichiers Web.config et les directives de page, et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> dans le code Visual Basic ou Visual C#. Le paramètre de culture détermine la mise en forme des valeurs telles que les dates, les nombres et les devises. La culture est définie en tant que `Culture` dans les fichiers Web.config et les directives de page, <xref:System.Globalization.CultureInfo.CurrentCulture%2A> dans le code Visual Basic ou Visual C#.

## <a name="see-also"></a>Voir aussi
 <xref:System.Globalization> <xref:System.Resources>
 [Globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md) [sécurité et assemblys satellites localisés](../ide/security-and-localized-satellite-assemblies.md)
