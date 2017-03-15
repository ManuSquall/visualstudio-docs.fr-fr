---
title: "Langues de relation contenant-contenus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - relation contenant-contenu de langues"
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Langues de relation contenant-contenus
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Les langages contenus* sont des langages contenus par d'autres langages.  Par exemple, HTML dans les pages de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] peut contenir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou des scripts de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] .  Une architecture de double\-langage est requise pour que l'éditeur de fichiers .aspx afin de fournir Intellisense, la colorisation, et d'autres fonctionnalités de modification du HTML et le langage de script.  
  
## Implémentation  
 L'interface la plus importante que vous devez implémenter pour les langages contenus est l'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> .  Cette interface est implémentée par n'importe quel langage qui peut être hébergé dans une langue principale.  Il permet d'accéder au coloriseur du service de langage, le filtre d'affichage de texte, et à l'identification de service de langage principale  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> vous permet de créer une interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> .  Les étapes suivantes montrent comment implémenter un langage contenu :  
  
1.  Utilisez `QueryService()` pour obtenir l'ID de service de langage et l'ID d'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  appelez la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> pour créer une interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> .  Passez une interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , un ID d'élément \(un ou plusieurs des <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>, d' <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>, ou d' <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>\) et une interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> .  
  
3.  L'interface d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> , qui est l'objet distributed mémoire tampon de texte, fournit les services de base requis pour mapper des emplacements dans un fichier primaire dans la mémoire tampon de la langue secondaire.  
  
     Par exemple, dans un fichier .aspx unique, le fichier principal inclut ASP, HTML et tout le code qui est contenu.  Toutefois, la mémoire tampon secondaire, compose uniquement du code contenu, ainsi que toutes les définitions de classe, pour définir cette mémoire tampon secondaire un fichier valide de code.  Le coordinateur de mémoire tampon gère le travail des modifications coordonnées d'une mémoire tampon vers l'autre.  
  
4.  La méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> , qui est la langue principale, indique au coordinateur de mémoire tampon le texte dans sa mémoire tampon est mappé au texte correspondant dans la mémoire tampon secondaire.  
  
     Le langage passe un tableau de la structure d' <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> , qui inclut actuellement qu'une étendue principale et secondaire.  
  
5.  la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> et la méthode d' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> fournissent le mappage de primaire à la mémoire tampon secondaire et vice versa.