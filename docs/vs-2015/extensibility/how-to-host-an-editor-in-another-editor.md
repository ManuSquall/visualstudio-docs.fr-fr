---
title: 'Comment : héberger un éditeur dans un autre éditeur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4b4ff425feb22b5057a8d1a76b7f73b8932d9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204173"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Guide pratique pour héberger un éditeur dans un autre éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez héberger un éditeur dans un autre en spécifiant la fenêtre d’hébergement comme fenêtre parente. Pour ce faire, définissez les paramètres <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> et <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> sur le frame de fenêtre enfant.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Pour configurer le frame de fenêtre pour héberger un éditeur  
  
1. Désignez un éditeur en tant qu’éditeur hébergé en créant un volet de fenêtre enfant.  
  
     Ce volet est l’endroit où se trouve le texte de l’éditeur.  
  
2. Créez l’éditeur d’hébergement à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> méthode ou.  
  
3. Définissez les <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> Propriétés et dans l’implémentation du frame de fenêtre de l’éditeur hébergé en passant ces propriétés en tant que paramètres à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> méthode, respectivement.  
  
     Si vous devez récupérer ces paramètres, transmettez ces propriétés à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> méthode.  
  
4. Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> méthode pour l’éditeur contenu.  
  
     L’éditeur s’affiche dans le volet hébergé de l’éditeur conteneur.  
  
## <a name="robust-programming"></a>Programmation fiable  
 L' **Concepteur d’applications** dans Visual Studio Team Edition for Architects est un exemple de frame de fenêtre d’éditeur qui héberge un autre éditeur. Le **Concepteur d’applications** héberge d’autres concepteurs dans son volet de droite. Un panneau de conception (ou une page de **Propriétés** ) pour chacun des concepteurs contenus est ajouté au frame de fenêtre conteneur.
