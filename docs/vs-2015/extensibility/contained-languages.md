---
title: Langues contenues | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0920999eee7460c8bf697e245bae55a3641b8e18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184278"
---
# <a name="contained-languages"></a>Langues incluses
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

Les *langages contenus* sont des langues qui sont contenues dans d’autres langages. Par exemple, le code HTML dans les [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pages peut contenir des [!INCLUDE[csprcs](../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] scripts ou. Une architecture à deux langages est nécessaire pour que l’éditeur de fichier. aspx fournisse IntelliSense, la colorisation et d’autres fonctionnalités d’édition pour le langage HTML et le langage de script.  
  
## <a name="implementation"></a>Implémentation  
 L’interface est l’interface la plus importante que vous devez implémenter pour les langages contenus <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> . Cette interface est implémentée par n’importe quel langage qui peut être hébergé dans une langue principale. Il donne accès au Coloriseur du service de langage, au filtre d’affichage de texte et à l’ID du service de langage principal. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>Vous permet de créer une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Les étapes suivantes vous montrent comment implémenter un langage contenu :  
  
1. Utilisez `QueryService()` pour récupérer l’ID du service de langage et l’ID d’interface du <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> .  
  
2. Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> méthode pour créer une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Passer une <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface, un ou plusieurs [ID d’élément](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) et une <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface.  
  
3. L' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface, qui est l’objet coordinateur de mémoire tampon de texte, fournit les services de base requis pour mapper les emplacements d’un fichier primaire dans la mémoire tampon du langage secondaire.  
  
     Par exemple, dans un seul fichier. aspx, le fichier primaire contient les pages ASP, HTML et tout le code contenu. Toutefois, la mémoire tampon secondaire comprend uniquement le code contenu, ainsi que toutes les définitions de classe, pour que la mémoire tampon secondaire soit un fichier de code valide. Le coordinateur de tampons gère le travail de coordination des modifications d’une mémoire tampon à l’autre.  
  
4. La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> méthode, qui est la langue principale, indique au coordinateur de mémoire tampon quel texte dans sa mémoire tampon est mappé au texte correspondant dans la mémoire tampon secondaire.  
  
     Le langage passe dans un tableau de la <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> structure, qui comprend actuellement uniquement une étendue principale et une étendue secondaire.  
  
5. La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> méthode et la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> méthode fournissent le mappage de la mémoire tampon principale à la mémoire tampon secondaire et vice versa.
