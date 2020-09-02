---
title: SccGetVersion fonction) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4e548f1f2b82a97206cdf41174a8c1c7d61e885
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200049"
---
# <a name="sccgetversion-function"></a>Fonction SccGetVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction obtient le numéro de version de l’API de plug-in de contrôle de code source pris en charge par le plug-in de contrôle de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="return-value"></a>Valeur renvoyée  
 `LONG`Type de données qui contient le numéro de version de l’API de plug-in de contrôle de code source pris en charge :  
  
|WORD|Description|  
|----------|-----------------|  
|HIWORD|Version principale|  
|LOWORD|Version secondaire|  
  
## <a name="remarks"></a>Notes  
 Par exemple, si un plug-in de contrôle de code source prend en charge la version 1,3 de l’API de plug-in de contrôle de code source, cette fonction retourne 0x0103.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
