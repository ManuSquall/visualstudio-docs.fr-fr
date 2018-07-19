---
title: Fonction de SccGetVersion | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70beb89f13d2f752f3adb0f25e2b370fa272171a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136443"
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
  
## <a name="remarks"></a>Notes  
 Par exemple, si un plug-in de contrôle de code source prend en charge la version 1.3 de l’API de plug-in de contrôle de Source, cette fonction retourne 0x0103.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)