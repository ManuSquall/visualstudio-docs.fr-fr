---
title: Managed Package Framework Classes | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: douge
ms.openlocfilehash: 931e73af72d2239ec04ac248b9fa426fe24f249a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188992"
---
# <a name="managed-package-framework-classes"></a>Classes MPF (Managed Package Framework)
Les classes MPF (Managed Package Framework) peuvent servir à créer des VSPackages à l’aide de code managé. Elles fournissent des implémentations par défaut pour de nombreuses interfaces VSPackage. En masquant les détails et la complexité d’une implémentation, MPF vous permet de créer des produits d’intégration [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] avec un minimum de code.  
  
> [!WARNING]
>  La plupart des assemblys qui contiennent des classes MPF sont fournis avec le Kit de développement Visual Studio (SDK). Vous pouvez télécharger le code source de Managed Package Framework for Projects ici : [Managed Package Framework for Projects](http://mpfproj11.codeplex.com/).  
  
## <a name="mpf-namespaces"></a>Espaces de noms MPF  
 Le tableau suivant répertorie les espaces de noms MPF fournis par le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
|Espace de noms|Sommaire|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|Contient des classes utiles pour la gestion des erreurs COM, des constantes [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et des fenêtres Win32.|  
|<xref:Microsoft.VisualStudio.Package>|Inclut les wrappers de code managé pour les projets [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , les éditeurs et MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell>|Inclut les classes de base MPF à partir desquelles vous pouvez dériver une implémentation de nombreux objets Visual Studio courants.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Contient des extensions de concepteur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Contient des extensions de concepteur de sérialisation [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Contient des extensions de concepteur CodeDom [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Prend en charge les sous-types de projet (également appelés « configurations »).|  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages et infrastructure de Package gérée](../misc/vspackages-and-the-managed-package-framework.md)   
 [À l’aide des assemblys d’interopérabilité Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackages et infrastructure de package gérée](../misc/vspackages-and-the-managed-package-framework.md)