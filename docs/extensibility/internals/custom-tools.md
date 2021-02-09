---
title: Outils personnalisés | Microsoft Docs
description: Apprenez à créer des outils personnalisés dans Visual Studio qui associent un outil à un élément dans un projet et exécutez cet outil à chaque fois que le fichier est enregistré.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7fdadad602a256b4740b4c4204704ca73864d612
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903023"
---
# <a name="custom-tools"></a>Outils personnalisés
Les *outils personnalisés* vous permettent d’associer un outil à un élément d’un projet et d’exécuter cet outil à chaque fois que le fichier est enregistré. Certains outils personnalisés, parfois appelés « *générateurs de fichiers uniques »*, sont souvent utilisés pour implémenter des traducteurs qui génèrent du code à partir de données, et vice versa. Par exemple, les générateurs de fichier unique créent [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] le code source à partir des fichiers *. Settings* et *. resx* . Le code source généré fournit un accès fortement typé aux données dans les fichiers *. Settings* et *. resx* . Les [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] types de projets et prennent en charge les outils personnalisés [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] . Vos propres types de projets peuvent également prendre en charge des outils personnalisés.

 Les outils personnalisés sont des composants inscrits qui implémentent l' `IVsSingleFileGenerator` interface.

 Les outils personnalisés sont associés à un `ProjectItem` objet d’interface et sont similaires aux concepteurs et aux éditeurs. Un outil personnalisé prend le fichier représenté par un `ProjectItem` comme entrée et écrit un nouveau fichier dont le nom de fichier est fourni par la `DefaultExtension` méthode.

## <a name="in-this-section"></a>Dans cette section
- [Implémenter des générateurs de fichiers uniques](../../extensibility/internals/implementing-single-file-generators.md)

 Décrit comment utiliser l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface pour implémenter un outil personnalisé.

- [Inscrire des générateurs de fichiers uniques](../../extensibility/internals/registering-single-file-generators.md)

 Fournit des descriptions pour toutes les entrées de registre d’un outil personnalisé.

- [Exposer des types à des concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Explique comment les systèmes de projet fournissent la prise en charge des concepteurs visuels pour accéder aux classes et aux types générés par le biais de fichiers PE (Portable Executable) temporaires.

- [Rendre persistante la propriété d’un élément de projet](../../extensibility/persisting-the-property-of-a-project-item.md)

 Montre comment rendre persistante une propriété d’élément de projet, telle que l’auteur d’un fichier source, dans le fichier projet.

## <a name="reference"></a>Référence
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Fournit des détails sur le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> , qui transforme un fichier d’entrée unique en un seul fichier de sortie qui peut être compilé ou ajouté à un projet.

 <xref:EnvDTE.ProjectItem> Explique l' `ProjectItem` interface, qui représente un élément dans un projet.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> Fournit des détails sur la `DefaultExtension` méthode, qui récupère l’extension de nom de fichier qui est donnée au nom du fichier de sortie.

## <a name="related-sections"></a>Sections connexes
- [Étendre des projets](../../extensibility/extending-projects.md)

 Décrit comment utiliser des projets et des solutions [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour organiser des fichiers de code et de ressources, et comment implémenter le contrôle de code source.
