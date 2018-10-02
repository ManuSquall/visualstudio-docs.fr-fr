---
title: IDiaFrameData::get_lengthSavedRegisters | Microsoft Docs
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
- IDiaFrameData::get_lengthSavedRegisters method
ms.assetid: dfda4e91-9bfa-4b9d-9133-b73015bfa4d5
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7a06e788f8dbd16825d6f508749227dc8477fab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502153"
---
# <a name="idiaframedatagetlengthsavedregisters"></a>IDiaFrameData::get_lengthSavedRegisters
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDiaFrameData::get_lengthSavedRegisters](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters).  
  
Récupère le nombre d’octets de l’objet d’un push sur la pile de registres enregistrés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_lengthSavedRegisters (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le nombre d’octets de registres enregistrés.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 La valeur retournée par cette méthode est généralement utilisée dans l’interprétation d’une chaîne de programme (voir la [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) méthode pour la définition d’une chaîne de programme).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)



