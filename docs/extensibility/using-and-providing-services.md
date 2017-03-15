---
title: "À l’aide et de fournir des Services | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 41
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: fb380330420d6256190ade75e0afe89f8cbda303
ms.lasthandoff: 02/22/2017

---
# <a name="using-and-providing-services"></a>À l’aide et fournir des Services
Un service est un contrat entre les deux packages VS. Un VSPackage offre un ensemble spécifique d’interfaces pour un autre VSPackage à consommer. Par exemple, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offre la <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog>service à n’importe quel package VS charges.</xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> Ce service fournit l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>interface, qui peut être utilisé pour écrire dans le journal d’activité.</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Pour plus d’informations, consultez [Comment : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
 Les VSPackages peuvent proposer des services de leurs propres à l’aide de l' <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>interface...</xref:Microsoft.VisualStudio.Shell.Interop.IProfferService>  
  
 Visual Studio offre des services importants, tels que les éléments suivants :  
  
|Service de l’IDE|Description|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fournit l’accès à l’IDE services traiter avec les fonctionnalités de base, les VSPackages et le Registre.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fournit le fenêtrage de base et les fonctionnalités associées à l’interface utilisateur dans l’IDE, telles que la possibilité de créer des outils et des fenêtres de document.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution></xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fournit des fonctionnalités de liés à la solution de base, comme la possibilité d’énumérer des projets, créer des projets et surveiller les modifications du projet.|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Service Essentials](../extensibility/internals/service-essentials.md)  
 Présente les éléments importants d’un service de Visual Studio.  
  
 [Comment : obtenir un Service](../extensibility/how-to-get-a-service.md)  
 Explique comment demander (consommer) un service.  
  
 [Comment : fournir un Service](../extensibility/how-to-provide-a-service.md)  
 Explique comment fournir un service.  
  
 [Comment : fournir un Service asynchrone Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Explique comment fournir un service asynchrone.  
  
 [Comment : résoudre les problèmes des Services](../extensibility/how-to-troubleshoot-services.md)  
 Aborde les problèmes courants et présente des solutions pour eux.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [SDK Visual Studio](../extensibility/visual-studio-sdk.md)
