---
title: Contenus de langues | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce2079ce16ac339ae536430d02d546ea39ffae0a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874000"
---
# <a name="contained-languages"></a>Langues de relation contenant-contenus

*Langues de contenus* sont des langages qui sont contenus par d’autres langages. Par exemple, le code HTML dans [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pages peuvent contenir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] scripts. Une architecture de double-language est requise pour le *.aspx* fonctionnalités de l’éditeur de fichier pour fournir IntelliSense, la colorisation et autres modification pour le code HTML et le langage de script.

## <a name="implementation"></a>Implémentation

L’interface plus importantes que vous devez implémenter pour les langages contenus est le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Cette interface est implémentée par n’importe quel langage peut être hébergé dans une langue principale. Il permet d’accéder pour le service de langage Coloriseur, filtre de vue de texte et ID de service de langage principal. Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> vous permet de créer un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Les étapes suivantes vous montrent comment implémenter un langage de relation contenant-contenu :

1.  Utilisez `QueryService()` pour obtenir la langue des ID de service et l’ID de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.

2.  Pour créer un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> l’interface, appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> (méthode). Passer un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface, un ou plusieurs [d’élément ID](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)et un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface.

3.  Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface, qui est l’objet coordinateur de mémoire tampon de texte, fournit les services de base qui sont requises pour mapper les emplacements dans un fichier primaire dans la mémoire tampon de langage secondaire.

     Par exemple, dans un seul *.aspx* fichier, le fichier primaire inclut l’ASP, HTML et tout le code qui est contenu. Toutefois, la mémoire tampon secondaire inclut uniquement le code de relation contenant-contenu avec les définitions de classe, pour rendre la mémoire tampon secondaire à un fichier de code valide. Le coordinateur de mémoire tampon gère le travail de coordination des modifications d’une mémoire tampon à l’autre.

4.  Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> (méthode), qui est la langue principale, indique au coordinateur de mémoire tampon de texte dans sa mémoire tampon est mappé au texte correspondant dans la mémoire tampon secondaire.

     Le langage passe dans un tableau de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> structure incluant actuellement uniquement un serveur principal et une étendue secondaire.

5.  Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> (méthode) et le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> méthode fournit le mappage principal vers une mémoire tampon secondaire et vice versa.