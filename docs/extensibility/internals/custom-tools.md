---
title: Outils personnalisés | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c192128ff4995a551b50df9347981405e321b703
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933228"
---
# <a name="custom-tools"></a>Outils personnalisés
*Outils personnalisés* vous permettent d’associer un outil à un élément dans un projet et d’exécuter cet outil chaque fois que le fichier est enregistré. Certains des outils personnalisés, parfois appelé *générateurs de fichier unique*, sont fréquemment utilisées pour implémenter des traducteurs qui génèrent du code à partir des données et vice versa. Par exemple, créent des générateurs de fichier unique [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] source code hors de la *.settings* et *.resx* fichiers. Le code source généré fournit l’accès fortement typé aux données dans le *.settings* et *.resx* fichiers. Le [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] types de projets prend en charge des outils personnalisés ; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] n’est pas le cas des types de projets. Vos propres types de projet peuvent prendre également en charge des outils personnalisés.  
  
 Les outils personnalisés sont des composants qui implémentent la `IVsSingleFileGenerator` interface.  
  
 Outils personnalisés sont associés un `ProjectItem` objet d’interface et sont comme les éditeurs et concepteurs. Un outil personnalisé prend le fichier représenté par un `ProjectItem` comme entrée et écrit un nouveau fichier dont le nom est fourni par le `DefaultExtension` (méthode).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Implémenter des générateurs de fichier unique](../../extensibility/internals/implementing-single-file-generators.md)  
 Décrit comment utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface à implémenter un outil personnalisé.  
  
 [Enregistrer un fichier unique générateurs](../../extensibility/internals/registering-single-file-generators.md)  
 Fournit des descriptions pour toutes les entrées de Registre pour un outil personnalisé.  
  
 [Exposer des types aux concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Explique comment projet fournissent une assistance pour les concepteurs visuels pour les types et les classes d’accès généré via des fichiers temporaires exécutable portable (PE).  
  
 [Rendre persistante la propriété d’un élément de projet](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Montre comment conserver une propriété d’élément de projet, telles que l’auteur d’un fichier source, dans le fichier projet.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Fournit des détails sur la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, qui transforme un fichier d’entrée unique en un seul fichier de sortie qui peut être compilé ou ajouté à un projet.  
  
 <xref:EnvDTE.ProjectItem>  
 Explique le `ProjectItem` interface, qui représente un élément dans un projet.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Fournit des détails sur la `DefaultExtension` (méthode), qui Récupère l’extension de nom de fichier qui est attribuée au nom du fichier de sortie.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Étendre des projets](../../extensibility/extending-projects.md)  
 Décrit comment utiliser des projets et des solutions [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour organiser des fichiers de code et de ressources, et comment implémenter le contrôle de code source.