---
title: IDiaSymbol::get_backEndBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndBuild method
ms.assetid: 423af497-9294-438e-92b4-456c6f56dc56
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1bd7a0bc75907d60a3ac3cbb8a571908631777e3
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "91838503"
---
# <a name="idiasymbolget_backendbuild"></a>IDiaSymbol::get_backEndBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Récupère le numéro de build back end du compilateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT get_backEndBuild (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 à Retourne le numéro de build du back end. Consultez la section Notes.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
> Une valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
 Un compilateur se compose généralement de deux éléments principaux : le serveur frontal (l’analyseur), qui gère l’analyse du code source dans un formulaire intermédiaire et un back end (générateur de code), qui convertit le formulaire intermédiaire en assembly. Il n’est pas rare que le serveur frontal ait une version différente de celle du back end.  
  
 Un numéro de version frontale ou de back end est composé de trois parties : \<major> . \<minor> . \<build> , où \<major> est le numéro de version principale, \<minor> est le numéro de version mineure et \<build> est le numéro de Build. Par exemple, 13.10.3077.  
  
## <a name="requirements"></a>Configuration requise  
  
|Condition requise|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v 7.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
