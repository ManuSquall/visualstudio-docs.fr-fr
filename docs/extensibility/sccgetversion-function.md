---
title: Fonction de SccGetVersion | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetVersion
helpviewer_keywords: SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f64b1412d0750bba4d3985d33286915e22f1474
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="sccgetversion-function"></a>SccGetVersion (fonction)
Cette fonction obtient le numéro de version de l’API de plug-in de contrôle de Source pris en charge par le plug-in de contrôle de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="return-value"></a>Valeur de retour  
 A `LONG` type de données qui contient le numéro de version de l’API de plug-in du contrôle Source pris en charge :  
  
|WORD|Description|  
|----------|-----------------|  
|HIWORD|Version principale|  
|LOWORD|Version mineure|  
  
## <a name="remarks"></a>Remarques  
 Par exemple, si un plug-in de contrôle de code source prend en charge la version 1.3 de l’API de plug-in de contrôle de Source, cette fonction retourne 0x0103.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)