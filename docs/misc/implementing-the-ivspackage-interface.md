---
title: "Impl&#233;mentation de l’interface IVsPackage | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface IVsPackage"
  - "interfaces, implémentation IVsPackages"
ms.assetid: 0c76b2e1-ce63-47fc-93ee-847cad281fc1
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Impl&#233;mentation de l’interface IVsPackage
Tous les VSPackages doit implémenter l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> .  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] appelle les méthodes d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> pour initialiser et fermer les VSPackages, pour obtenir les pages de propriétés associées, et pour d'autres raisons.  L'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> est l'interface de la passerelle entre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et un VSPackage.  
  
 Vous pouvez écrire un VSPackage managé comme une sous\-classe de la classe d' <xref:Microsoft.VisualStudio.Shell.Package> , qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> sur votre nom.  Pour plus d'informations, consultez [VSPackages gérés](../misc/managed-vspackages.md).  
  
> [!NOTE]
>  Une grande partie de l'exemple de code non managé dans la section d'intégration Visual Studio de [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] utilise ATL \(ATL\).  Vous n'avez pas besoin d'utiliser ATL pour créer les VSPackages, mais vous devez comprendre ATL pour inclure l'exemple de code.  
  
## Voir aussi  
 [Packages VS](../extensibility/internals/vspackages.md)