---
title: Outils personnalisés (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e60f1d8cb8b25ed50b0b20c5ebb538286687ad72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708956"
---
# <a name="custom-tools"></a>Outils personnalisés
*Les outils personnalisés* vous permettent d’associer un outil à un élément d’un projet et d’exécuter cet outil chaque fois que le fichier est enregistré. Certains outils *personnalisés,* parfois appelés générateurs à fichiers uniques, sont fréquemment utilisés pour implémenter des traducteurs qui génèrent du code à partir de données et vice versa. Par exemple, les générateurs [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] à fichiers uniques créent et approvisionnent le code des fichiers *.settings* et *.resx.* Le code source généré fournit un accès fortement typé aux données dans les fichiers *.settings* et *.resx.* Les [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] types de projet et de projet prennent en charge les outils personnalisés; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] les types de projets ne le font pas. Vos propres types de projets peuvent également prendre en charge des outils personnalisés.

 Les outils personnalisés sont `IVsSingleFileGenerator` des composants enregistrés qui implémentent l’interface.

 Les outils personnalisés `ProjectItem` sont associés à un objet d’interface, et sont comme les concepteurs et les éditeurs. Un outil personnalisé prend le `ProjectItem` fichier représenté par une entrée et écrit `DefaultExtension` un nouveau fichier dont le nom de fichier est fourni par la méthode.

## <a name="in-this-section"></a>Contenu de cette section
- [Mettre en œuvre des générateurs à fichiers uniques](../../extensibility/internals/implementing-single-file-generators.md)

 Décrit comment utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> l’interface pour implémenter un outil personnalisé.

- [Enregistrez les générateurs de fichiers uniques](../../extensibility/internals/registering-single-file-generators.md)

 Fournit des descriptions pour toutes les entrées de registre pour un outil personnalisé.

- [Exposer les types à des concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Explique comment les systèmes de projet fournissent un soutien aux concepteurs visuels pour accéder aux classes et aux types générés par le biais de fichiers portables temporaires exécutables (PE).

- [Persévérer dans la propriété d’un élément de projet](../../extensibility/persisting-the-property-of-a-project-item.md)

 Montre comment persévérer dans le dossier du projet, comme l’auteur d’un fichier source.

## <a name="reference"></a>Informations de référence
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>Fournit des <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>détails sur le , qui transforme un fichier d’entrée unique en un seul fichier de sortie qui peut être compilé ou ajouté à un projet.

 <xref:EnvDTE.ProjectItem>Explique `ProjectItem` l’interface, qui représente un élément dans un projet.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>Fournit des `DefaultExtension` détails sur la méthode, qui récupère l’extension du nom de fichier qui est donnée au nom du fichier de sortie.

## <a name="related-sections"></a>Sections connexes
- [Étendre les projets](../../extensibility/extending-projects.md)

 Décrit comment utiliser des projets et des solutions [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour organiser des fichiers de code et de ressources, et comment implémenter le contrôle de code source.
