---
title: "À l’aide et de fournir des Services | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: "41"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fbba5070af77e1509ed3b3840a2045ae0f2c12b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-and-providing-services"></a>À l’aide et fournir des Services
Un service est un contrat entre deux VSPackages. Un VSPackage offre un ensemble spécifique d’interfaces pour un autre VSPackage à consommer. Par exemple, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offre la <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service à un VSPackage de charge. Ce service fournit le <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface, ce qui peut être utilisé pour écrire dans le journal d’activité. Pour plus d’informations, consultez [Comment : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
 Les VSPackages peuvent offrir des services de leurs propres à l’utilisation de la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface...  
  
 Visual Studio offre des services importants, tels que les éléments suivants :  
  
|Service de l’IDE|Description|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fournit des accès à l’IDE de services de traitement avec les fonctionnalités de base, des VSPackages et le Registre.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fournit des fonctionnalités associées à l’interface utilisateur dans l’IDE, telles que la capacité à créer des outils et des fenêtres de document et base de fenêtrage.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fournit les fonctionnalités basiques associés à la solution, notamment la possibilité d’énumérer les projets, créer des projets et surveiller les modifications de projet.|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md)  
 Présente les éléments importants d’un service de Visual Studio.  
  
 [Guide pratique pour obtenir un service](../extensibility/how-to-get-a-service.md)  
 Explique comment demander (consommer) un service.  
  
 [Guide pratique pour fournir un service](../extensibility/how-to-provide-a-service.md)  
 Explique comment fournir un service.  
  
 [Guide pratique pour fournir un service Visual Studio asynchrone](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Explique comment fournir un service asynchrone.  
  
 [Guide pratique pour dépanner les services](../extensibility/how-to-troubleshoot-services.md)  
 Aborde les problèmes courants et indique des solutions à ceux-ci.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [SDK Visual Studio](../extensibility/visual-studio-sdk.md)