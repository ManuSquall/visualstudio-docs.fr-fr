---
title: IDiaEnumDebugStreams::Item | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumDebugStreams::Item method
ms.assetid: 6b388fe1-eabc-4720-9d59-dc09b0ceaeac
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fefec4989c649e7b4113f78948c1ce30d42f050f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumdebugstreamsitem"></a>IDiaEnumDebugStreams::Item
Récupère un flux de débogage au moyen d’un index ou un nom.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT Item (   
   VARIANT                   index,  
   IDiaEnumDebugStreamData** stream  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 index  
 [in] Index ou le nom du flux de débogage doit être récupéré. Si un Variant de type integer est utilisé, il doit être comprise entre 0 et `count`-1, où `count` est renvoyé par le [IDiaEnumDebugStreams::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreams-get-count.md) (méthode).  
  
 flux de données  
 [out] Retourne un [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) objet qui représente le flux de débogage spécifiés.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
  
```C++  
IDiaEnumDebugStreamData *GetStreamData(IDiaEnumDebugStreams *pStreamList,  
                                       LONG whichStream)  
{  
    IDiaEnumDebugStreamData *pStreamData = NULL;  
    if (pStreamList != NULL)  
    {  
        LONG numStreams = 0;  
        if (pStreamList->get_count(&numStreams) == S_OK &&  
            whichStream >= 0 && whichStream < numStreams)  
        {  
            VARIANT vIndex;  
            vIndex.vt   = VT_I4;  
            vIndex.lVal = whichStream;  
            if (pStreamList->Item(vIndex,&pStreamData) != S_OK)  
            {  
                 std::cerr << "Error retrieving stream " << whichStream << std::endl;  
            }  
        }  
    }  
    return(pStreamData);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)