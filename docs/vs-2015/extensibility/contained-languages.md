---
title: Contenus de langues | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 22f297027d2196cf69c241f651fd84cbb18ecfa1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184962"
---
# <a name="contained-languages"></a>Langues de relation contenant-contenus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

  
*Langues de contenus* sont des langages qui sont contenus par d’autres langages. Par exemple, le code HTML dans [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pages peuvent contenir [!INCLUDE[csprcs](../includes/csprcs-md.md)] ou [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] scripts. Une architecture de double-language est requise pour l’éditeur de fichier .aspx fournir IntelliSense, la colorisation et autres fonctionnalités d’édition pour le code HTML et le langage de script.  
  
## <a name="implementation"></a>Implémentation  
 L’interface plus importantes que vous devez implémenter pour les langages contenus est le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Cette interface est implémentée par n’importe quel langage peut être hébergé dans une langue principale. Il permet d’accéder pour le service de langage Coloriseur, filtre de vue de texte et ID de service de langage principal. Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> vous permet de créer un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Les étapes suivantes vous montrent comment implémenter un langage de relation contenant-contenu :  
  
1.  Utilisez `QueryService()` pour obtenir la langue des ID de service et l’ID de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> méthode pour créer un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Passer un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface, un ou plusieurs [d’élément ID](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) et un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface.  
  
3.  Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface, qui est l’objet coordinateur de mémoire tampon de texte, fournit les services de base qui sont requises pour mapper les emplacements dans un fichier primaire dans la mémoire tampon de langage secondaire.  
  
     Par exemple, dans un fichier .aspx unique, le fichier primaire inclut l’ASP, HTML et tout le code qui est contenu. Toutefois, la mémoire tampon secondaire, inclut uniquement le code relation contenant-contenu, ainsi que des définitions de classe, pour rendre la mémoire tampon secondaire à un fichier de code valide. Le coordinateur de mémoire tampon gère le travail de coordination des modifications d’une mémoire tampon à l’autre.  
  
4.  Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> (méthode), qui est la langue principale, indique au coordinateur de mémoire tampon de texte dans sa mémoire tampon est mappé au texte correspondant dans la mémoire tampon secondaire.  
  
     Le langage passe dans un tableau de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> structure incluant actuellement uniquement un serveur principal et une étendue secondaire.  
  
5.  Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> (méthode) et le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> méthode fournit le mappage principal vers une mémoire tampon secondaire et vice versa.

