---
title: Déploiement des prérequis pour les Applications 64 bits | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 3f416a22bc7cbdd374622c89a1826ebff8af9450
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950081"
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>Composants requis pour le déploiement d'applications 64 bits
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le déploiement ClickOnce prend en charge l'installation des applications sur les plateformes 64 bits. Les plateformes cibles sont de type **x86** pour les plateformes 32 bits, **x64** pour les machines prenant en charge les jeux d’instructions AMD64 et EM64T, et **Itanium** pour le processeur Itanium 64 bits.  
  
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
 [Guide pratique pour Installer les composants requis avec une Application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Applications 64 bits](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)
