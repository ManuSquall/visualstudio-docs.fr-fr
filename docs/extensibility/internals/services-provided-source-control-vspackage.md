---
title: Services fournis (VSPackage de contrôle de code source) | Microsoft Docs
description: Découvrez comment les VSPackages partagent les fonctionnalités par le biais de services, y compris l’interaction avec l’IDE de Visual Studio et ses VSPackages.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fe1d9ee9805e6e86595f3f7f3cf640114c7030b9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080812"
---
# <a name="services-provided-source-control-vspackage"></a>Services fournis (VSPackage de contrôle de code source)
Les services sont le mécanisme principal par le biais duquel les fonctionnalités sont partagées entre les VSPackages et entre l’environnement de développement intégré (IDE) de Visual Studio et les VSPackages installés. Pour obtenir une description détaillée des services et leur importance dans l’IDE de Visual Studio, consultez[utilisation et fourniture de services](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>Le service de contrôle de code source
 Visual Studio fournit deux couches de services, les services de niveau IDE et les services au niveau du package. L’IDE de Visual Studio fournit en mode natif des services de niveau IDE. Le package de contrôle de code source utilise certains de ces services. Le package de contrôle de code source en tant que VSPackage partage ses fonctionnalités de contrôle de code source en fournissant un service de contrôle de code source privé propre. Le package de contrôle de code source encapsule l’ensemble des interfaces relatives au contrôle de code source implémentées par celui-ci sous la forme d’un contrat qui peut être utilisé par l’IDE de Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Éléments de conception](../../extensibility/internals/source-control-vspackage-design-elements.md)
