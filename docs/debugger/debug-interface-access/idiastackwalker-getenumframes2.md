---
title: IDiaStackWalker::getEnumFrames2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fb7fff92007160abdba64970d652ee73042661b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938131"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
Récupère un énumérateur de frame de pile pour un type de plateforme spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cpuid`  
 [in] Une valeur comprise entre le [CV_CPU_TYPE_e (énumération)](../../debugger/debug-interface-access/cv-cpu-type-e.md) énumération spécifiant le type de plateforme.  
  
 `pHelper`  
 [in] Le programme d’assistance [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) objet.  
  
 `ppEnum`  
 [out] Retourne un [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) objet contenant une liste de [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) objets.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 Pour obtenir une liste de frames de pile pour simplement le x86 plateforme, appelez le [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [CV_CPU_TYPE_e, énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)