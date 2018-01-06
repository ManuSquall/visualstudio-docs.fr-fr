---
title: "Comment : héberger un éditeur dans un autre éditeur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 685ad1d619fdf9f04fe1a9cd1122a9e6ed3ba025
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Comment : héberger un éditeur dans un autre éditeur
Dans Visual Studio, vous pouvez héberger un seul éditeur à l’intérieur d’un autre en spécifiant la fenêtre hôte comme une fenêtre parente. Pour ce faire, définissez les paramètres <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> et <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> sur le frame de fenêtre enfant.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Pour définir le frame de fenêtre pour héberger un éditeur  
  
1.  Désigner un éditeur comme un éditeur hébergé par la création d’un volet de fenêtre enfant.  
  
     Ce volet se trouve dans lequel passe de texte de l’éditeur.  
  
2.  Créer l’éditeur d’hébergement à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> (méthode).  
  
3.  Définir le <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> et <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> propriétés dans l’implémentation du frame de fenêtre de l’Éditeur hébergé en transmettant ces propriétés comme paramètres pour la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> (méthode), respectivement.  
  
     Si vous avez besoin récupérer ces paramètres, de ces propriétés pour transmettre le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> (méthode).  
  
4.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> méthode pour l’éditeur de relation contenant-contenu.  
  
     L’éditeur apparaît dans le volet hébergé de l’éditeur de conteneur.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Le **Concepteur d’applications** dans Visual Studio Team Edition for Architects est un exemple d’un frame de fenêtre d’éditeur qui héberge un autre éditeur. Le **Concepteur d’applications** héberge d’autres concepteurs dans son volet de droite. Un panneau concepteur (ou **propriétés** page) pour chacun des concepteurs contenus est ajouté à la fenêtre frame contenant.