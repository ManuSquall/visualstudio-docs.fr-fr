---
title: "Services fournis (VSPackage de contrôle de code Source) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c30c374756578fd71dd344393b58f38cacadeb19
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="services-provided-source-control-vspackage"></a>Services fournis (VSPackage de contrôle de code Source)
Les services sont le mécanisme principal par l’intermédiaire duquel la fonctionnalité est partagée entre les VSPackages et entre l’environnement de développement intégré (IDE) Visual Studio et son VSPackages installés. Pour obtenir une description détaillée des services et leur importance dans l’IDE de Visual Studio, consultez[à l’aide et fourniture de Services](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Le Service de contrôle de code Source  
 Visual Studio fournit deux couches de services, les services au niveau de l’IDE et les services au niveau du package. En mode natif, l’IDE de Visual Studio fournit des services au niveau de l’IDE. Le package de contrôle de code source utilise certains de ces services. Le package de contrôle de source en tant que VSPackage partage ses fonctionnalités de contrôle de code source en fournissant un service de contrôle de source privée de son propre. Le package de contrôle de code source encapsule le jeu d’interfaces de relatifs au contrôle de source implémentée par sous la forme d’un contrat qui peut être utilisé par l’IDE Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments de conception.](../../extensibility/internals/source-control-vspackage-design-elements.md)