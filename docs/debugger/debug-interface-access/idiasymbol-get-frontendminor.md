---
title: IDiaSymbol::get_frontEndMinor | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_frontEndMinor method
ms.assetid: 40792153-827c-4859-be7c-6aa16d5abab6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30bfe092ed8454b14a7e26d77b375c75cabc0836
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetfrontendminor"></a>IDiaSymbol::get_frontEndMinor
Récupère le numéro de version mineure du front-end.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_frontEndMinor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le numéro de version mineure front.end.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Remarques  
 Un compilateur est généralement constitué de deux éléments principaux : le serveur frontal (analyseur), qui gère l’analyse du code source en un format intermédiaire, et un serveur principal (Générateur de code), qui convertit le formulaire intermédiaire dans l’assembly. Il n’est pas rare pour le serveur frontal d’avoir une version différente de celle du serveur principal.  
  
 Un frontal ou un numéro de version principale se compose de trois parties : \<majeure >.\< mineure >. \<Générer >, où \<majeure > est le numéro de version principale, \<mineure > est le numéro de version mineure et \<Générer > est le numéro de build. Par exemple, 13.10.3077.  
  
## <a name="requirements"></a>Spécifications  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v7.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)