---
title: Fourniture d’une fenêtre de propriétés personnalisées | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: a244463832ff5620efa74a2c7fd20d6d47d79e76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62810698"
---
# <a name="providing-a-custom-properties-window"></a>Fourniture d’une fenêtre de propriétés personnalisée
Il est possible de fournir votre propre fenêtre de **Propriétés** pour un système de projet donné, au lieu d’étendre la fenêtre **Propriétés** fournie par l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] environnement de développement intégré (IDE). Le scénario le plus souvent rencontré est le moment où vous implémentez vous-même l’objet dans le frame de fenêtre.  
  
 Si vous n’implémentez pas l’objet sur site dans le frame de fenêtre, mais que vous y avez toujours accès par d’autres moyens, il existe plusieurs façons d’accéder à l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interface, comme indiqué dans la dernière procédure de cette page.  
  
### <a name="to-provide-your-properties-window"></a>Pour fournir votre Fenêtre Propriétés  
  
1. Définissez un GUID qui représente l’implémentation de votre fenêtre de **Propriétés** .  
  
2. Dans votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implémentation, utilisez le <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> service pour offrir votre fenêtre de **Propriétés** en tant que service à l’environnement Visual Studio.  
  
### <a name="to-call-your-properties-window"></a>Pour appeler la fenêtre Propriétés  
  
1. Appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> .  
  
2. `QueryService` pour <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> à partir du <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> passé dans la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> méthode.  
  
3. Obtenir <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> à partir du <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> service.  
  
4. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> avec le premier paramètre défini sur `SEID_PropertyBrowserSID` (extrait de l' <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> énumération) et le troisième paramètre, `varValue` , représentant une forme de chaîne du GUID qui représente la fenêtre de **Propriétés** . Effectuez cet appel une seule fois lors de la première création de la fenêtre de document de la fenêtre **Propriétés** . Une fois que l’appel de cette fenêtre de **Propriétés** est associé à votre frame de fenêtre.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>Pour obtenir l’objet de frame de fenêtre lorsque vous n’êtes pas l’implémenteur  
  
- `QueryService`Pour <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> le service, vous pouvez <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> utiliser avec le paramètre `propid` défini sur <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> .  
  
- Vous pouvez obtenir la fenêtre de document active en appelant par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> biais du service SVsMonitorSelection. Affectez au paramètre la valeur `elementid` `SEID_WindowFrame` , extraite de l' <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des propriétés](../extensibility/internals/extending-properties.md)   
 [Champs et interfaces de la fenêtre Propriétés](../extensibility/internals/properties-window-fields-and-interfaces.md)