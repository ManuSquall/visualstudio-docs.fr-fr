---
title: IDiaSymbol::get_frontEndMajor | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_frontEndMajor method
ms.assetid: f8a067c5-3306-4fc5-bc20-8910a47ed504
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67d6a614ebac95809050a9f4ceb8201e7d76ee36
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetfrontendmajor"></a>IDiaSymbol::get_frontEndMajor
Récupère le numéro de version majeure du front-end.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_frontEndMajor (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne le numéro de version majeure du front-end. Consultez la section Notes.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
> [!NOTE]
>  La valeur de retour `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.  
  
## <a name="remarks"></a>Notes  
 Un compilateur est généralement constitué de deux éléments principaux : le serveur frontal (analyseur), qui gère l’analyse du code source en un format intermédiaire, et un serveur principal (Générateur de code), qui convertit le formulaire intermédiaire dans l’assembly. Il n’est pas rare pour le serveur frontal d’avoir une version différente de celle du serveur principal.  
  
 Un frontal ou un numéro de version principale se compose de trois parties : \<majeure >.\< mineure >. \<Générer >, où \<majeure > est le numéro de version principale, \<mineure > est le numéro de version mineure et \<Générer > est le numéro de build. Par exemple, 13.10.3077.  
  
## <a name="requirements"></a>Spécifications  
  
|Spécification|Description|  
|-----------------|-----------------|  
|En-tête :|dia2.h|  
|Version :|DIA SDK v7.0|  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)