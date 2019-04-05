---
title: À l’aide et de fourniture de Services | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f58e29797e9a7760aa0f48c68868199f51b3c92
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948041"
---
# <a name="using-and-providing-services"></a>Utilisation et fourniture de services
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un service est un contrat entre deux VSPackages. Un VSPackage offre un ensemble spécifique d’interfaces pour un autre package Visual Studio consommer. Par exemple, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] offre la <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service à n’importe quel package VS de charges. Ce service fournit le <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface, ce qui peut être utilisé pour écrire dans le journal d’activité. Pour plus d'informations, voir [Procédure : Utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).  
  
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
  
 [Guide pratique pour Bénéficiez d’un Service](../extensibility/how-to-get-a-service.md)  
 Explique comment demander (consommer) un service.  
  
 [Guide pratique pour Fournir un Service](../extensibility/how-to-provide-a-service.md)  
 Explique comment fournir un service.  
  
 [Guide pratique pour Fournir un Service asynchrone Visual Studio](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md)  
 Explique comment fournir un service asynchrone.  
  
 [Guide pratique pour Résoudre les problèmes des Services](../extensibility/how-to-troubleshoot-services.md)  
 Aborde les problèmes courants et présente des solutions pour eux.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md)
