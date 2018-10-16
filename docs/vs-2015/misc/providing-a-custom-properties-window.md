---
title: Fourniture d’une fenêtre de propriétés personnalisées | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: douge
ms.openlocfilehash: 8b3aeae11e087b6a6bd662ed32564d93062426df
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186275"
---
# <a name="providing-a-custom-properties-window"></a>Fourniture d’une fenêtre de propriétés personnalisée
Il est possible de fournir votre propre **propriétés** fenêtre pour un système de projet donné, au lieu de l’extension de la **propriétés** fenêtre fournie par le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] l’environnement de développement intégré (IDE). Le scénario plus fréquemment rencontré est lorsque vous devez implémentez l’objet que doit se trouver dans le frame de fenêtre.  
  
 Dans l’événement vous n’implémentez pas l’objet doit se trouver dans le frame de fenêtre, mais que vous avez toujours accès à celui-ci par d’autres moyens, il existe plusieurs façons d’accéder à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> comme indiqué dans la dernière procédure dans cette page de l’interface.  
  
### <a name="to-provide-your-properties-window"></a>Pour fournir votre fenêtre de propriétés  
  
1.  Définir un GUID qui représente votre **propriétés** implémentation de la fenêtre.  
  
2.  Dans votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implémentation, utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> service à mettre en avant votre **propriétés** fenêtre en tant que service à l’environnement Visual Studio.  
  
### <a name="to-call-your-properties-window"></a>Pour appeler votre fenêtre de propriétés  
  
1.  Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A>.  
  
2.  `QueryService` pour <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> à partir de la <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> passé dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> (méthode).  
  
3.  Obtenir <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> de <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> service.  
  
4.  Appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> avec le premier paramètre défini sur `SEID_PropertyBrowserSID` (extraites de la <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> énumération) et le troisième paramètre, `varValue`, représentant une forme de chaîne du GUID qui représente votre **propriétés** fenêtre. Rendre cet appel une seule fois lors de la première création de votre **propriétés** fenêtre de document. Après l’appel de cette **propriétés** fenêtre est associée à votre frame de fenêtre.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>Pour obtenir l’objet de Frame de fenêtre lorsque vous n’êtes pas l’implémenteur  
  
-   Vous pouvez `QueryService` pour <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> service <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> avec le paramètre `propid` défini sur <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>.  
  
-   Vous pouvez obtenir la fenêtre de document actif en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> via SVsMonitorSelection service. Définissez le paramètre `elementid` à `SEID_WindowFrame`, effectuée à partir de la <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre les propriétés](../extensibility/internals/extending-properties.md)   
 [Champs et interfaces de la fenêtre Propriétés](../extensibility/internals/properties-window-fields-and-interfaces.md)