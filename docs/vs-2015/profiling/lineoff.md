---
title: LineOff | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf55f34b1ced4d76dcd45ea08514dfbb04ca582b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502233"
---
# <a name="lineoff"></a>LineOff
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [LineOff](https://docs.microsoft.com/visualstudio/profiling/lineoff).  
  
Par défaut, le profileur collecte le numéro de ligne du code source et le décalage de numéro de ligne quand vous utilisez la méthode de profilage par échantillonnage. L’option **LineOff** de VSPerfCmd désactive la collecte des numéros de ligne quand VSPerfCmd est utilisé pour démarrer l’application. Les données de profilage sont collectées au niveau de la fonction quand **LineOff** est spécifié.  
  
 Vous pouvez utiliser **LineOff** seulement avec l’option **Launch**, et seulement quand le profileur a été initialisé pour l’échantillonnage avec l’option **Start**:**Sample**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="required-options"></a>Options obligatoires  
 L’option **LineOff** peut être utilisée seulement sur une ligne de commande qui contient l’option **Launch**.  
  
 **Launch :** `AppName`  
 Démarre l’application spécifiée et commence le profilage avec la méthode d’échantillonnage.  
  
## <a name="example"></a>Exemple  
 Cet exemple démarre l’application et le profileur, et désactive l’échantillonnage au niveau des lignes.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)



