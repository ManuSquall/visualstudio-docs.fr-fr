---
title: IEEDataStorage::GetData | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2e2430a6b2e8ae1a39882611e55499ebdb9bf4d8
ms.lasthandoff: 02/22/2017

---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Récupère le nombre spécifié d’octets à partir de l’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```c#  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dataSize`  
 [in] Le nombre d’octets à récupérer (la `data` tableau doit contenir au moins ce nombre d’octets).  
  
 `sizeGotten`  
 [out] Retourne le nombre d’octets réellement récupérées.  
  
 `data`  
 [dans, out] Tableau à remplir avec les données demandées.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 L’utilisation de cette méthode recommandée consiste à récupérer tous les octets de données dans un tableau local, dans la mesure où il n’existe aucun moyen d’ignorer les octets dans le processus de récupération. Dans ce cas, le paramètre `dataSize` doit être la valeur retournée par le [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
