---
title: IDispatchEx::DeleteMemberByName | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 5cb9a9dfd979954c42101fde41819d7e12db59e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728129"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Supprime un membre par son nom.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bstrName`  
 Nom du membre à supprimer.  
  
 `grfdex`  
 Détermine si le nom du membre respecte la casse. Cela peut prendre l’une des valeurs suivantes :  
  
|Valeur|Signification|  
|-----------|-------------|  
|fdexNameCaseSensitive|Demande que la recherche de nom faire de la casse. Peut être ignoré par l’objet qui ne prend pas en charge la recherche qui respecte la casse.|  
|fdexNameCaseInsensitive|Demande que la recherche de nom faire respecter la casse. Peut être ignoré par l’objet qui ne prend pas en charge la recherche sans respecter la casse.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne l’une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Opération réussie.|  
|`S_FALSE`|Membre existe mais ne peut pas être supprimé.|  
  
## <a name="remarks"></a>Remarques  
 Si le membre est supprimé, le DISPID doit rester valide pour `GetNextDispID`.  
  
 Si un membre avec un nom donné est supprimé, et par la suite un membre portant le même nom est recréé, le DISPID doit être le même. (Si les membres qui diffèrent uniquement par leur casse sont « même » est dépendant de l’objet.)  
  
## <a name="example"></a>Exemple  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)