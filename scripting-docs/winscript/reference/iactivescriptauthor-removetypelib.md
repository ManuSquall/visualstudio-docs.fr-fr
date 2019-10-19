---
title: 'IActiveScriptAuthor :: RemoveTypeLib | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.RemoveTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::RemoveTypeLib
ms.assetid: 232c3698-024d-4549-8fbc-cb0d3ac17dc5
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 182d13785b20f9c5ba298ab72cd8d28977d455ba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576135"
---
# <a name="iactivescriptauthorremovetypelib"></a>IActiveScriptAuthor::RemoveTypeLib
Supprime une bibliothèque de types de l’espace de noms du moteur de création de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT RemoveTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `rguidTypeLib`  
 dans CLSID (identificateur de classe) de la bibliothèque de types à supprimer.  
  
 `dwMajor`  
 dans Numéro de version principale.  
  
 `dwMinor`  
 dans Numéro de version mineure.  
  
## <a name="return-value"></a>Valeur de retour  
 Élément `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)