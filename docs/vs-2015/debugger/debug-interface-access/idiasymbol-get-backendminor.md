---
title: IDiaSymbol::get_backEndMinor | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 494d0b8311de61dcff3c6adbb5edbb46e01cb50e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49219126"
---
# <a name="idiasymbolgetbackendminor"></a>IDiaSymbol::get_backEndMinor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le numéro de version mineure de back-end du compilateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_backEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le numéro de version secondaire du serveur principal. Consultez la section Notes.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
 Un compilateur est généralement constitué de deux éléments principaux : le serveur frontal (analyseur), qui gère l’analyse du code source dans un format intermédiaire, et un back-end (Générateur de code), qui convertit le formulaire intermédiaire en assembly. Il n’est pas rare pour le serveur frontal avoir une version différente de celle du serveur principal.  
  
 Un serveur frontal ou le numéro de version de serveur principal est composé de trois parties : \<majeure >.\< mineure >. \<Générer >, où \<majeure > est le numéro de version principale, \<mineure > est le numéro de version mineure et \<Générer > est le numéro de build. Par exemple, 13.10.3077.  
  
## <a name="requirements"></a>Configuration requise  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v7.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



