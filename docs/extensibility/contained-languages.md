---
title: Contenu de langues | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bfdbc3d1c0e7bbc0b3dc712d9434ca1b49c6feca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="contained-languages"></a>Langues de relation contenant-contenus
*Contenu de langues* sont des langages qui sont contenus par d’autres langages. Par exemple, le code HTML dans [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pages peuvent contenir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] des scripts. Une architecture de double-language est requise pour l’éditeur de fichier .aspx fournir IntelliSense, la colorisation et autres fonctionnalités d’édition pour le code HTML et le langage de script.  
  
## <a name="implementation"></a>Implémentation  
 L’interface plus importante, vous devez implémenter des langues de relation contenant-contenus est le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Cette interface est implémentée par n’importe quel langage qui peut être hébergé dans une langue principale. Il donne accès à Coloriseur le service de langage, filtre de vue de texte et ID langue principale du service. Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> vous permet de créer un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Les étapes suivantes vous montrent comment implémenter un langage de relation contenant-contenu :  
  
1.  Utilisez `QueryService()` pour obtenir la langue d’ID de service et l’ID de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> méthode pour créer un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Passez un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> d’interface, un ID d’élément (une ou plusieurs des <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>, <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>, ou <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>) et un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface.  
  
3.  Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface, qui est l’objet de coordinateur de mémoire tampon de texte, fournit les services de base qui sont requises pour mapper les emplacements dans un fichier principal dans la mémoire tampon de la langue secondaire.  
  
     Par exemple, dans un fichier .aspx unique, le fichier primaire inclut ASP, HTML et tout le code qui est contenu. Toutefois, la mémoire tampon secondaire, inclut uniquement le code contenu, ainsi que les définitions de classe, pour rendre la mémoire tampon secondaire à un fichier de code valide. Le coordinateur de mémoires tampons gère les tâches de coordonner les modifications à partir d’une mémoire tampon à l’autre.  
  
4.  Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> (méthode), qui est la langue primaire, indique le coordinateur de la mémoire tampon au sein de sa mémoire tampon de texte est mappé au texte correspondant dans la mémoire tampon secondaire.  
  
     Le langage passe dans un tableau de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> structure, actuellement uniquement comprenant un serveur principal et un intervalle secondaire.  
  
5.  Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> (méthode) et le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> méthode fournit le mappage du serveur principal vers une mémoire tampon secondaire et vice versa.