---
title: "Contr&#244;le de glyphe (VSPackage du contr&#244;le de code Source) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "glyphes, packages de contrôle de code source"
  - "packages de contrôle de code source, glyphes"
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Contr&#244;le de glyphe (VSPackage du contr&#244;le de code Source)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Une partie de l'intégration profonde disponible au contrôle de code source VSPackages est la possibilité d'afficher leurs propres glyphes pour indiquer l'état des éléments sous contrôle de code source.  
  
## niveaux de contrôle de glyphe  
 Un glyphe d'état est une icône qui indique l'état actuel d'un élément en cas de rendu, par exemple dans **Explorateur de solutions** ou dans **Affichage de classes**.  Un contrôle de code source VSPackage peut avoir deux niveaux de contrôle de glyphe.  Elle peut limiter le choix des glyphes à un ensemble prédéfini de glyphes fournis par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE, ou elle peut définir un jeu personnalisé de glyphes à afficher.  
  
### La cible par défaut le jeu de glyphes  
 Pour déterminer les glyphes d'état qui sont associés à un élément dans **Explorateur de solutions**, demandes d'un projet le glyphe d'état du contrôle de code source à l'aide de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>.  Un contrôle de code source VSPackage peut décider de conserver le choix des glyphes limitent aux glyphes intégrés fournis par l'IDE.  Dans ce cas, les passes de VSPackage à un tableau de valeurs représentant les énumérations de glyphe qui sont définies dans vsshell.idl.  Pour plus d'informations, consultez l' <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Il s'agit d'un ensemble prédéfini de glyphes définis par l'IDE, tel qu'un cadenas pour « signé » le glyphe, et une coche comme « vérifié » glyphe.  
  
### personnalisé défini des glyphes  
 Un contrôle de code source VSPackage peut utiliser ses propres glyphes pour une unique « apparence » lorsqu'elle est installée.  Lorsqu'un nouveau contrôle de code source VSPackage est actif, il doit pouvoir commencer à utiliser ses propres glyphes même si un contrôle de code source précédent VSPackage est chargé mais inactif.  Dans ce mode, le contrôle de code source VSPackage peut toujours utiliser les icônes existantes pour conserver un être compatible avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] s'il choisit.  
  
 Le service prend en charge d' <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> une interface, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, que le VSPackage peut éventuellement implémenter et qui sera pas par l'IDE.  Lorsque l'IDE établit une demande, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tente ensuite d'obtenir cette interface du contrôle de code source actuellement inscrit VSPackage.  Si l'interface existe dans le VSPackage enregistré, la demande de l'IDE de glyphes personnalisés aboutit ; sinon, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE utilise son ensemble par défaut des glyphes.  
  
 La méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> est utilisée par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour obtenir une liste d'images affichage de différents états du contrôle de code source.  Le contrôle de code source VSPackage retourne à l'IDE un handle à la liste d'images pour ses glyphes personnalisés.  L'IDE crée une copie de la liste d'images à ce stade et l'utiliser ultérieurement pour choisir les glyphes à afficher.  Si la nouvelle interface n'est pas prise en charge la méthode ou de `IVsSccGlyphs::GetCustomGlyphList` retourne E\_NOTIMPL, alors l'IDE obtient ses glyphes de la liste par défaut de glyphes fournis par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>