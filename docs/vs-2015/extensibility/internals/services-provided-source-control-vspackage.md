---
title: Services fournis (VSPackage de contrôle de code Source) | Microsoft Docs
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
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aff288f68f32d3850cfa92d5999febd1c65572e1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504434"
---
# <a name="services-provided-source-control-vspackage"></a>Services fournis (VSPackage de contrôle de code source)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [les Services fournis (VSPackage de contrôle de code Source)](https://docs.microsoft.com/visualstudio/extensibility/internals/services-provided-source-control-vspackage).  
  
Les services sont le mécanisme principal via lequel la fonctionnalité est partagée entre les VSPackages et entre l’environnement de développement intégré (IDE) Visual Studio et ses VSPackage installés. Pour obtenir une description détaillée des services et leur importance dans l’IDE Visual Studio, consultez[utilisation et fourniture de Services](../../extensibility/using-and-providing-services.md).  
  
## <a name="the-source-control-service"></a>Le Service de contrôle de Source  
 Visual Studio fournit deux couches de services, les services au niveau de l’IDE et les services au niveau du package. En mode natif, l’IDE Visual Studio fournit des services au niveau de l’IDE. Le package de contrôle de code source utilise certains de ces services. Le package de contrôle de code source en tant que VSPackage partage ses fonctionnalités de contrôle de code source en fournissant un service de contrôle de source privée qui lui sont propres. Le package de contrôle de code source encapsule le jeu d’interfaces de relatifs au contrôle de source implémentée par ce dernier sous la forme d’un contrat qui peut être utilisé par l’IDE Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments de conception](../../extensibility/internals/source-control-vspackage-design-elements.md)

