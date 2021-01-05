---
title: Utilisation et fourniture de services | Microsoft Docs
description: Découvrez les services que l’IDE de Visual Studio propose pour les VSPackages à fournir et utiliser. Ces articles décrivent comment obtenir et fournir des services.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6a7c1d9f3632d8b710ac238c372ed4456183a8d1
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715936"
---
# <a name="using-and-providing-services"></a>Utilisation et fourniture de services
Un service est un contrat entre deux VSPackages. Un VSPackage offre un ensemble spécifique d’interfaces à utiliser par un autre VSPackage. Par exemple, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offre le <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> service à tout VSPackage qu’il charge. Ce service fournit l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interface, qui peut être utilisée pour écrire dans le journal d’activité. Pour plus d’informations, consultez [procédure : utiliser le journal d’activité](../extensibility/how-to-use-the-activity-log.md).

 Les VSPackages peuvent offrir leurs propres services à l’aide de l' <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> interface.

 Visual Studio offre des services importants, tels que les suivants :

|Service IDE|Description|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Permet d’accéder aux services IDE traitant des fonctionnalités de base, des VSPackages et du Registre.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fournit des fonctionnalités de base de fenêtrage et d’interface utilisateur dans l’IDE, telles que la possibilité de créer des outils et des fenêtres de document.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fournit des fonctionnalités de base relatives à la solution, telles que la possibilité d’énumérer des projets, de créer de nouveaux projets et de surveiller les modifications apportées au projet.|

## <a name="in-this-section"></a>Dans cette section
- [Notions de service Essentials](../extensibility/internals/service-essentials.md) Présente les éléments importants d’un service Visual Studio.

- [Comment : obtenir un service](../extensibility/how-to-get-a-service.md) Explique comment demander (consommer) un service.

- [Comment : fournir un service](../extensibility/how-to-provide-a-service.md) Explique comment fournir un service.

- [Comment : fournir un service Visual Studio asynchrone](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) Explique comment fournir un service asynchrone.

- [Comment : dépanner des services](../extensibility/how-to-troubleshoot-services.md) Décrit les problèmes courants et leur propose des solutions.

## <a name="related-sections"></a>Sections connexes
- [SDK Visual Studio](../extensibility/visual-studio-sdk.md)
