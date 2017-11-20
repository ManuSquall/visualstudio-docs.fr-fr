---
title: IDiaStackWalkHelper::put_registerValue | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8abfd209e5c2f59a0c55128eb235fda868f4bfd5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
## <a name="remarks"></a>Remarques  
 En dépit de la taille de la valeur, une implémentation doit stocker uniquement ce que le Registre maintient. Par exemple, un Registre de 8 bits contiendrait uniquement les 8-bits les plus bas de la valeur donnée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e (énumération)](../../debugger/debug-interface-access/cv-hreg-e.md)