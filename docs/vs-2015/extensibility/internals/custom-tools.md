---
title: Outils personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72fb6f9f0ceb3b9f2ae04f39b2c37c416acf47b9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501680"
---
# <a name="custom-tools"></a>Outils personnalisés
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [outils personnalisés](https://docs.microsoft.com/visualstudio/extensibility/internals/custom-tools).  
  
*Outils personnalisés* vous permettent d’associer un outil à un élément dans un projet et d’exécuter cet outil chaque fois que le fichier est enregistré. Certains des outils personnalisés, parfois appelé *générateurs de fichier unique*, sont fréquemment utilisées pour implémenter des traducteurs qui génèrent du code à partir des données et vice versa. Par exemple, créent des générateurs de fichier unique [!INCLUDE[csprcs](../../includes/csprcs-md.md)] et [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] code hors les fichiers .settings et .resx source. Le code source généré fournit un accès fortement typé aux données dans les fichiers .settings et .resx. Le [!INCLUDE[csprcs](../../includes/csprcs-md.md)] et [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] types de projets prend en charge des outils personnalisés ; [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] n’est pas le cas des types de projets. Vos propres types de projet peuvent prendre également en charge des outils personnalisés.  
  
 Les outils personnalisés sont des composants qui implémentent la `IVsSingleFileGenerator` interface.  
  
 Outils personnalisés sont associés un `ProjectItem` objet d’interface et sont comme les éditeurs et concepteurs. Un outil personnalisé prend le fichier représenté par un `ProjectItem` comme entrée et écrit un nouveau fichier dont le nom est fourni par le `DefaultExtension` (méthode).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Implémentation de générateurs de fichier unique](../../extensibility/internals/implementing-single-file-generators.md)  
 Décrit comment utiliser le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface à implémenter un outil personnalisé.  
  
 [Détermination de l’espace de noms par défaut d’un projet](../../misc/determining-the-default-namespace-of-a-project.md)  
 Décrit comment déterminer l’espace de noms correct en fonction de la langue utilisée.  
  
 [Inscription de générateurs de fichier unique](../../extensibility/internals/registering-single-file-generators.md)  
 Fournit des descriptions pour toutes les entrées de Registre pour un outil personnalisé.  
  
 [Exposition des types aux concepteurs visuels](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Explique comment projet fournissent une assistance pour les concepteurs visuels pour les types et les classes d’accès généré via des fichiers temporaires exécutable portable (PE).  
  
 [Conservation de la propriété d’un élément de projet](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Montre comment conserver une propriété d’élément de projet, telles que l’auteur d’un fichier source, dans le fichier projet.  
  
## <a name="reference"></a>Référence  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Fournit des détails sur la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, qui transforme un fichier d’entrée unique en un seul fichier de sortie qui peut être compilé ou ajouté à un projet.  
  
 <xref:EnvDTE.ProjectItem>  
 Explique le `ProjectItem` interface, qui représente un élément dans un projet.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Fournit des détails sur la `DefaultExtension` (méthode), qui Récupère l’extension de nom de fichier qui est attribuée au nom du fichier de sortie.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Extension des projets](../../extensibility/extending-projects.md)  
 Décrit comment utiliser [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projets et solutions possibles pour organiser les fichiers de code et les fichiers de ressources et comment implémenter le contrôle de code source.

