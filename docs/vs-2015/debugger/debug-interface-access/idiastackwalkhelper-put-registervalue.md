---
title: IDiaStackWalkHelper::put_registerValue | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4936d33150f38ed84a03b1d3a1b661bdb402bb64
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493297"
---
# <a name="idiastackwalkhelperputregistervalue"></a>IDiaStackWalkHelper::put_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaStackWalkHelper::put_registerValue](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkhelper-put-registervalue).  
  
Définit la valeur d’un Registre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `index`  
 [in] Une valeur comprise entre le [CV_HREG_e (énumération)](../../debugger/debug-interface-access/cv-hreg-e.md) énumération spécifiant le Registre pour écrire dans.  
  
 `NewVal`  
 [in] La nouvelle valeur de Registre.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 En dépit de la taille de la valeur, une implémentation doit stocker uniquement ce que le Registre normalement conserve. Par exemple, un Registre de 8 bits contiendrait uniquement les 8-bits les plus bas de la valeur donnée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e, énumération](../../debugger/debug-interface-access/cv-hreg-e.md)



