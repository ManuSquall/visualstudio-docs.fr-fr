---
title: IDiaEnumFrameData::get__NewEnum | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumFrameData::get__NewEnum method
ms.assetid: f5fe0279-0549-4af5-8f89-bcb535fc5809
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee374a7248390da11f689cb2568b3769c64aaf66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumframedatagetnewenum"></a>IDiaEnumFrameData::get__NewEnum
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
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)