---
title: Des outils personnalisés | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5f215cfbd5113377e7a98439976a7f44215eee02
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="custom-tools"></a>Outils personnalisés
*Des outils personnalisés* vous permettent d’associer un outil avec un élément dans un projet et d’exécuter cet outil chaque fois que le fichier est enregistré. Certains des outils personnalisés, parfois appelée *générateurs de fichier unique*, sont fréquemment utilisées pour implémenter les convertisseurs qui génèrent du code à partir des données et vice versa. Par exemple, créent des générateurs de fichier unique [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] source code les fichiers .settings et .resx. Le code source généré fournit un accès fortement typé aux données dans les fichiers .settings et .resx. Le [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] des types de projet prend en charge des outils personnalisés ; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] types de projets ne sont pas. Vos propres types de projet peuvent prendre également en charge des outils personnalisés.  
  
 Les outils personnalisés sont des composants qui implémentent la `IVsSingleFileGenerator` interface.  
  
 Des outils personnalisés sont associés un `ProjectItem` objet d’interface et sont similaires aux concepteurs et éditeurs. Un outil personnalisé prend le fichier représenté par un `ProjectItem` en entrée et écrit un nouveau fichier dont le nom est fourni par le `DefaultExtension` (méthode).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Implémentation de générateurs de fichier unique](../../extensibility/internals/implementing-single-file-generators.md)  
 Décrit comment utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface à implémenter un outil personnalisé.  
  
 [Inscription de générateurs de fichier unique](../../extensibility/internals/registering-single-file-generators.md)  
 Fournit des descriptions pour les entrées de Registre pour un outil personnalisé.  
  
 [Exposition des types aux concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Explique comment les systèmes de projet prennent en charge pour les concepteurs visuels pour les classes d’accès généré et les types dans les fichiers temporaires fichier exécutable portable (PE).  
  
 [Conservation de la propriété d’un élément de projet](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Montre comment conserver une propriété d’élément de projet, telles que l’auteur d’un fichier source, dans le fichier projet.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Fournit des détails sur la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, qui transforme un fichier d’entrée unique en un seul fichier de sortie qui peut être compilé ou ajouté à un projet.  
  
 <xref:EnvDTE.ProjectItem>  
 Explique la `ProjectItem` interface qui représente un élément dans un projet.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Fournit des détails sur la `DefaultExtension` méthode qui Récupère l’extension de nom de fichier pour le nom de fichier de sortie.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Extension des projets](../../extensibility/extending-projects.md)  
 Décrit comment utiliser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projets et solutions possibles pour organiser les fichiers de code et les fichiers de ressources et comment implémenter le contrôle de code source.