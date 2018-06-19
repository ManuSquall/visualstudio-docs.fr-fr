---
title: IDiaStackWalkHelper::put_registerValue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c094384fd4c1e01b28edcc809d58ab56b3bb225
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31463941"
---
# <a name="idiastackwalkhelperputregistervalue"></a>IDiaStackWalkHelper::put_registerValue
Définit la valeur d’un Registre.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `index`  
 [in] Une valeur à partir de la [CV_HREG_e (énumération)](../../debugger/debug-interface-access/cv-hreg-e.md) énumération spécifiant le Registre dans lequel écrire.  
  
 `NewVal`  
 [in] La nouvelle valeur de Registre.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En dépit de la taille de la valeur, une implémentation doit stocker uniquement ce que le Registre maintient. Par exemple, un Registre de 8 bits contiendrait uniquement les 8-bits les plus bas de la valeur donnée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e (énumération)](../../debugger/debug-interface-access/cv-hreg-e.md)