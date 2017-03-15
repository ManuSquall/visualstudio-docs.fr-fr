---
title: "Vue d’ensemble de la personnalisation | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Boîte de dialogue À propos de"
  - "VSPackages, écrans de démarrage"
  - "VSPackages, personnalisation"
ms.assetid: a47b3645-574c-41c7-8a97-d071cd6b1e82
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# Vue d’ensemble de la personnalisation
Pour afficher les informations sur le produit dans l'écran de démarrage ou la boîte de dialogue de **À propos de** , votre VSPackage doit procéder comme suit :  
  
-   Fournir un détaillé des informations sur le produit sous la clé de Registre d'InstalledProducts.  
  
     ou  
  
-   Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>.  
  
 Managed package \(MPF\) fournit l'attribut d' <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> à l'inscription du contrôle sous la clé de Registre d'InstalledProducts.  Pour plus d'informations, consultez [Comment : personnaliser un VSPackage \(C\# et Visual Basic\)](../misc/how-to-brand-a-vspackage-csharp-and-visual-basic.md).  
  
 La bibliothèque Visual Studio fournit la classe de modèle d' `IVsInstalledProductImpl` pour créer une implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>.  Pour plus d'informations, consultez [Procédure : personnalisation d’un VSPackage \(C\+\+\)](../misc/how-to-brand-a-vspackage-cpp.md).  
  
 Implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> est explicitement plus puissant que l'utilisation de l'attribut ou le modèle.  
  
-   vous pouvez spécifier une icône d'écran de démarrage qui diffère de l'icône de **À propos de** .  
  
-   Vous pouvez spécifier un nom de produit de l'écran de démarrage qui diffère du nom de produit de **À propos de** .  
  
    > [!IMPORTANT]
    >  Si vous utilisez <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> et implémentent également <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>, l'interface est prioritaire.  
  
    > [!NOTE]
    >  la même ressource icône est utilisée pour l'écran de démarrage et la boîte de dialogue de **À propos de** .  Votre ressource icône en VSPackage doit inclure 16 une image du x 16 pour l'écran de démarrage et 32 une image du x 32 pour la boîte de dialogue de **À propos de** .  Si vous fournissez uniquement une taille de l'image, il sera redimensionnée selon les besoins, mais les résultats visuels sont suboptimaux.  
  
 Pour obtenir une liste de tâches, consultez [Packages VS](../extensibility/internals/vspackages.md).  
  
## Voir aussi  
 [Packages VS](../extensibility/internals/vspackages.md)   
 [Vue d’ensemble de la bibliothèque Visual Studio](../misc/visual-studio-library-overview.md)