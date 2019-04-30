---
title: Fonction SccGetVersion | Microsoft Docs
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
ms.openlocfilehash: 7e2b3818aaa5097313d9150b365544267768507f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62802560"
---
# <a name="sccgetversion-function"></a>Fonction SccGetVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction obtient le numéro de version de l’API de plug-in de contrôle de Source pris en charge par le plug-in de contrôle de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="return-value"></a>Valeur de retour  
 Un `LONG` type de données qui contient le numéro de version de l’API de plug-in de contrôle de Source pris en charge :  
  
|WORD|Description|  
|----------|-----------------|  
|HIWORD|Version principale|  
|LOWORD|Version mineure|  
  
## <a name="remarks"></a>Notes  
 Par exemple, si un plug-in de contrôle de code source prend en charge la version 1.3 de l’API de plug-in de contrôle de Source, cette fonction retournait 0x0103.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
