---
title: IDiaEnumSourceFiles::get__NewEnum | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSourceFiles::get__NewEnum method
ms.assetid: 8405966c-64b4-4743-9a83-0e27ca2047c7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1a9627d7c4d5e4cdf1305ab4f4793903fdc439d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsourcefilesgetnewenum"></a>IDiaEnumSourceFiles::get__NewEnum
Récupère le <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> version de cet énumérateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pRetVal  
 [out] Retourne le `IUnknown` interface qui représente le <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> version de cet énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)