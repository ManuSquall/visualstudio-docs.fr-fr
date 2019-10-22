---
title: IDispatchEx ::D eleteMemberByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2abb562f65885ee1d12f2ec9b2300fcddd3be37b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576617"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Supprime un membre par son nom.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bstrName`  
 Nom du membre à supprimer.  
  
 `grfdex`  
 Détermine si le nom du membre respecte la casse. Il peut s’agir de l’une des valeurs suivantes :  
  
|valeur|Signification|  
|-----------|-------------|  
|fdexNameCaseSensitive|Demande que la recherche de nom s’effectue de façon sensible à la casse. Peut être ignoré par un objet qui ne prend pas en charge la recherche qui respecte la casse.|  
|fdexNameCaseInsensitive|Demande que la recherche de nom s’effectue sans respect de la casse. Peut être ignoré par un objet qui ne prend pas en charge la recherche ne respectant pas la casse.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Opération réussie.|  
|`S_FALSE`|Le membre existe mais ne peut pas être supprimé.|  
  
## <a name="remarks"></a>Notes  
 Si le membre est supprimé, le DISPID doit rester valide pour `GetNextDispID`.  
  
 Si un membre avec un nom donné est supprimé et qu’un membre du même nom est recréé, le DISPID doit être le même. (Si les membres qui diffèrent uniquement par la casse sont « identiques » dépend de l’objet).  
  
## <a name="example"></a>Exemple  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)