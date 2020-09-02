---
title: IDiaFrameData::get_lengthParams | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthParams method
ms.assetid: a9177ed6-9ba8-4384-b411-24cad07d031b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f633fe4633ba92b1054aec7f516a6a0921bc64ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62563713"
---
# <a name="idiaframedataget_lengthparams"></a>IDiaFrameData::get_lengthParams
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le nombre d’octets de paramètres faisant l’objet d’un push sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_lengthParams (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Retourne le nombre d’octets de paramètres.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas prise en charge. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 La valeur retournée par cette méthode est généralement utilisée dans l’interprétation d’une chaîne de programme (consultez la méthode [IDiaFrameData :: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) pour la définition d’une chaîne de programme).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
