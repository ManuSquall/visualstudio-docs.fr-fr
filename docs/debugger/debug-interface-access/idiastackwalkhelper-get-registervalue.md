---
title: IDiaStackWalkHelper::get_registerValue | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: dac8991fa31aae0ba65b0377e159b20256c4a416
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkhelpergetregistervalue"></a>IDiaStackWalkHelper::get_registerValue
Récupère la valeur d’un Registre.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `index`  
 [in] Une valeur à partir de la [cv_hreg_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md) énumération spécifiant permettant d’obtenir la valeur de Registre.  
  
 `pRetVal`  
 [out] Retourne la valeur actuelle du Registre.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En dépit de la taille de la `pRetVal` paramètre, une implémentation doit stocker uniquement ce que le Registre maintient. Par exemple, un Registre de 8 bits conserve uniquement les 8-bits les plus bas de la valeur donnée. Cette valeur de 8 bits est développée à 64-bits lorsque retournée par cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e (énumération)](../../debugger/debug-interface-access/cv-hreg-e.md)