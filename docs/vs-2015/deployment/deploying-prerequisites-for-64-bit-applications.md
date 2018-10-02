---
title: Déploiement des prérequis pour les Applications 64 bits | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 0f98a611b382f3884ede2e1e239944b9e584ab77
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502217"
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>Composants requis pour le déploiement d'applications 64 bits
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [déploiement des composants requis pour les Applications 64 bits](https://docs.microsoft.com/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications).  
  
Le déploiement ClickOnce prend en charge l'installation des applications sur les plateformes 64 bits. Les plateformes cibles sont **x86** pour les plateformes 32 bits, **x64** pour machines prenant en charge les jeux d’instructions AMD64 et EM64T, et **Itanium** pour le processeur Itanium 64 bits.  
  
## <a name="prerequisites"></a>Prérequis  
 Le tableau suivant répertorie les composants redistribuables que vous pouvez utiliser comme composants requis pour l'installation de votre application 64 bits.  
  
 Si vous sélectionnez un composant requis qui n'a pas de composants 64 bits, vous risquez de voir s'afficher un avertissement indiquant que les packages sélectionnés ne sont pas disponibles pour la plateforme 64 bits.  
  
|Composant redistribuable|Prise en charge x64|Prise en charge IA64|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../includes/vsto-runtime-md.md)]|Oui|Non|  
|Bibliothèques Runtime Visual C++ 2010 (IA64)|Non|Oui|  
|Bibliothèques Runtime Visual C++ 2010 (x64)|Oui|Non|  
|Microsoft .NET Framework 4 (x86 et x64)|Oui||  
|Microsoft .NET Framework 4 Client Profile (x86 et x64)|Oui||  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’applications, de services et de composants](../deployment/deploying-applications-services-and-components.md)   
 [Guide pratique pour installer des composants requis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Applications 64 bits](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)



