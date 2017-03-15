---
title: "Comment&#160;: forcer le chargement d’un package&#160;VS | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "packages VS, forcer le chargement"
  - "packages VS, charger"
ms.assetid: 05f4dc3f-3c9a-45ea-96da-986553b5c5f2
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# Comment&#160;: forcer le chargement d’un package&#160;VS
VSPackages sont couramment chargés uniquement lorsque les fonctionnalités ci\-dessous est requise pour terminer un processus.  Dans certains cas, toutefois, un VSPackage peut peut\-être forcer un autre VSPackage à charger.  Par exemple, un poids léger VSPackage peut charger un plus grand VSPackage dans un contexte de programmation qui n'est pas disponible comme CMDUIContext.  
  
 Vous pouvez utiliser la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> pour forcer un VSPackage pour charger.  
  
### pour forcer un VSPackage pour charger  
  
-   Insérez ce code dans la méthode d' <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> d'un VSPackage qui force un autre VSPackage pour charger :  
  
     [!code-cs[ForceVSPackageLoad#01](../misc/codesnippet/CSharp/how-to-force-a-vspackage-to-load_1.cs)]  
  
     Lorsque le VSPackage est initialisé, il forcera `PackageToBeLoaded` à charger.  
  
## Programmation fiable  
 Le chargement de force ne doit pas être utilisé pour la communication d'un VSPackage.  Utilisez plutôt [À l'aide et fournir des Services](../extensibility/using-and-providing-services.md).  
  
## Voir aussi  
 [La gestion de packages VS](../extensibility/managing-vspackages.md)   
 [Packages VS](../extensibility/internals/vspackages.md)