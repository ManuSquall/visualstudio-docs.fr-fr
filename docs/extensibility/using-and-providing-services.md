---
title: Utilisation et fourniture de services (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8741d8d66af96ad4c6abea44b238393a34c5aa95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698741"
---
# <a name="using-and-providing-services"></a>Utilisation et fourniture de services
Un service est un contrat entre deux VSPackages. Un VSPackage offre un ensemble spécifique d’interfaces pour un autre VSPackage à consommer. Par exemple, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> offre le service à n’importe quel VSPackage qu’il charge. Ce service <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> fournit l’interface, qui peut être utilisée pour écrire au journal d’activité. Pour plus d’informations, voir [Comment : Utilisez le journal d’activité](../extensibility/how-to-use-the-activity-log.md).

 VSPackages peut offrir des services <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> de leurs propres en utilisant l’interface..

 Visual Studio offre des services importants, tels que les suivants :

|Service IDE|Description|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Donne accès aux services IDE traitant des fonctionnalités de base, des VSPackages et du registre.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fournit des fenêtres de base et des fonctionnalités liées à l’interface utilisateur dans l’IDE, telles que la possibilité de créer des outils et de documenter les fenêtres.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fournit des fonctionnalités de base liées à la solution, telles que la possibilité d’énumérer des projets, de créer de nouveaux projets et de surveiller les changements de projets.|

## <a name="in-this-section"></a>Dans cette section
- [Essentiels de service](../extensibility/internals/service-essentials.md) Présente les éléments importants d’un service Visual Studio.

- [Comment : Obtenir un service](../extensibility/how-to-get-a-service.md) Discute de la façon de demander (consommer) un service.

- [Comment : Fournir un service](../extensibility/how-to-provide-a-service.md) Discute de la façon de fournir un service.

- [Comment : Fournir un service de studio visuel asynchrone](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Discute de la façon de fournir un service asynchrone.

- [Comment : Services de dépannage](../extensibility/how-to-troubleshoot-services.md) Discute des problèmes communs et leur présente des solutions.

## <a name="related-sections"></a>Sections connexes
- [SDK Visual Studio](../extensibility/visual-studio-sdk.md)
