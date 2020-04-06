---
title: Services fournis (Source Control VSPackage) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f08ebe49756b442ef474ac2a032a72894f6bec15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705409"
---
# <a name="services-provided-source-control-vspackage"></a>Services fournis (VSPackage de contrôle de code source)
Les services sont le principal mécanisme par lequel la fonctionnalité est partagée entre VSPackages et entre l’environnement de développement intégré Visual Studio (IDE) et ses VSPackages installés. Pour une description détaillée des services et leur importance dans le Visual Studio IDE, voir[Utilisation et Fournir des services](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Le service de contrôle des sources
 Visual Studio offre deux couches de services, des services au niveau de l’IDE et des services de forfait. Le Visual Studio IDE fournit nativement des services au niveau de l’IDE. Le paquet de contrôle source consomme certains de ces services. Le package de contrôle source en tant que VSPackage partage sa fonctionnalité de contrôle source en fournissant un service privé de contrôle source de ses propres. Le paquet de contrôle source résume l’ensemble d’interfaces de contrôle source mise en œuvre par lui sous la forme d’un contrat qui peut être utilisé par le Visual Studio IDE.

## <a name="see-also"></a>Voir aussi
- [Éléments de conception](../../extensibility/internals/source-control-vspackage-design-elements.md)
