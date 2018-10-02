---
title: À l’aide et de fourniture de Services | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: facf0bb9968e3ffbc9a68eb8eee906f300eb1859
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516574"
---
# <a name="using-and-providing-services"></a>Utilisation et fourniture de services
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [utilisation et fourniture de Services](https://docs.microsoft.com/visualstudio/extensibility/using-and-providing-services).  
  
Un service est un contrat entre deux VSPackages. Un VSPackage offre un ensemble spécifique d’interfaces pour un autre package Visual Studio consommer. Par exemple, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] offre la <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service à n’importe quel package VS de charges. Ce service fournit le <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface, ce qui peut être utilisé pour écrire dans le journal d’activité. Pour plus d’informations, consultez [Comment : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
 Les VSPackages peuvent offrir des services de façon autonome, à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface...  
  
 Visual Studio offre des services importants, tels que les éléments suivants :  
  
|Service de l’IDE|Description|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fournit l’accès à IDE services traiter avec des fonctionnalités de base, des VSPackages et le Registre.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fournit la base de fenêtrage et de fonctionnalités associées à l’interface utilisateur dans l’IDE, comme la possibilité de créer des outils et des fenêtres de document.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fournit des fonctionnalités de liées à la solution de base, telles que la possibilité d’énumérer des projets, créer des projets et surveiller les modifications du projet.|  
  
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
 Aborde les problèmes courants et présente des solutions pour eux.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [SDK Visual Studio](../extensibility/visual-studio-sdk.md)

