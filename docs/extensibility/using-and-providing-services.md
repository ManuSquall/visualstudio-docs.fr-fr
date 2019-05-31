---
title: À l’aide et de fourniture de Services | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c9b0dbf2122b5a76d557cdd70da27660b886041
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337037"
---
# <a name="using-and-providing-services"></a>Utilisation et fourniture de services
Un service est un contrat entre deux VSPackages. Un VSPackage offre un ensemble spécifique d’interfaces pour un autre package Visual Studio consommer. Par exemple, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offre la <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service à n’importe quel package VS de charges. Ce service fournit le <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface, ce qui peut être utilisé pour écrire dans le journal d’activité. Pour plus d'informations, voir [Procédure : Utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).

 Les VSPackages peuvent offrir des services de façon autonome, à l’aide de la <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface...

 Visual Studio offre des services importants, tels que les éléments suivants :

|Service de l’IDE|Description|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Fournit l’accès à IDE services traiter avec des fonctionnalités de base, des VSPackages et le Registre.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fournit la base de fenêtrage et de fonctionnalités associées à l’interface utilisateur dans l’IDE, comme la possibilité de créer des outils et des fenêtres de document.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fournit des fonctionnalités de liées à la solution de base, telles que la possibilité d’énumérer des projets, créer des projets et surveiller les modifications du projet.|

## <a name="in-this-section"></a>Dans cette section
- [Éléments fondamentaux du service](../extensibility/internals/service-essentials.md) présente les éléments importants d’un service de Visual Studio.

- [Guide pratique pour Obtenir un Service](../extensibility/how-to-get-a-service.md) explique comment demander (consommer) un service.

- [Guide pratique pour Fournir un Service](../extensibility/how-to-provide-a-service.md) explique comment fournir un service.

- [Guide pratique pour Fournir un Service de Visual Studio asynchrone](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) explique comment fournir un service asynchrone.

- [Guide pratique pour Dépanner les Services](../extensibility/how-to-troubleshoot-services.md) aborde les problèmes courants et présente des solutions pour eux.

## <a name="related-sections"></a>Rubriques connexes
- [Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk.md)