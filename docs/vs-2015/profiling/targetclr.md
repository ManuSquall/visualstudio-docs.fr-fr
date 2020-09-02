---
title: TargetCLR | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e4ca52f631b3e2de9c01daab7e6268c42f20268
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145623"
---
# <a name="targetclr"></a>TargetCLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’option **TargetCLR** spécifie la version du common language runtime (CLR) à profiler quand plusieurs versions du CLR sont chargées dans une application.  
  
 Par défaut, les Outils de profilage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ciblent la première version du CLR qui est chargée par l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Paramètres  
 `ClrVersion`  
 Numéro de version du CLR. Utilisez le format de version **vN.N.NNNNN**.  
  
## <a name="required-options"></a>Options obligatoires  
 L’option **TargetCLR** peut être utilisée seulement avec l’option **Launch** ou **Attach**.  
  
 **Lancer :**`AppName`  
 Démarre l’application spécifiée et démarre le profilage.  
  
 **Attacher :**`PID`  
 Démarre le profilage du processus spécifié.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, l’option TargetCLR est utilisée pour profiler la version 4.0.11003 du CLR.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```
