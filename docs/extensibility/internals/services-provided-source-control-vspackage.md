---
title: Services fournis (VSPackage de contrôle de code Source) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5cbc107b1b300538cf9a94a89a77d8ac9e2ff728
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828535"
---
# <a name="services-provided-source-control-vspackage"></a>Services fournis (VSPackage de contrôle de code source)
Les services sont le mécanisme principal via lequel la fonctionnalité est partagée entre les VSPackages et entre l’environnement de développement intégré (IDE) Visual Studio et ses VSPackage installés. Pour obtenir une description détaillée des services et leur importance dans l’IDE Visual Studio, consultez[utilisation et fourniture de Services](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Le Service de contrôle de Source  
 Visual Studio fournit deux couches de services, les services au niveau de l’IDE et les services au niveau du package. En mode natif, l’IDE Visual Studio fournit des services au niveau de l’IDE. Le package de contrôle de code source utilise certains de ces services. Le package de contrôle de code source en tant que VSPackage partage ses fonctionnalités de contrôle de code source en fournissant un service de contrôle de source privée qui lui sont propres. Le package de contrôle de code source encapsule le jeu d’interfaces de relatifs au contrôle de source implémentée par ce dernier sous la forme d’un contrat qui peut être utilisé par l’IDE Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments de conception](../../extensibility/internals/source-control-vspackage-design-elements.md)