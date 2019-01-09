---
title: IDispatchEx::DeleteMemberByName | Microsoft Docs
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
ms.openlocfilehash: 1866b5135d2c98ccacb34c2c776c69dd7d25db3f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096432"
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
 Détermine si le nom du membre respecte la casse. Cela peut prendre l’une des valeurs suivantes :  
  
|Value|Signification|  
|-----------|-------------|  
|fdexNameCaseSensitive|Demande que la recherche de nom faire de la casse. Peut être ignoré par l’objet qui ne prend pas en charge la recherche respectant la casse.|  
|fdexNameCaseInsensitive|Demande que la recherche de nom être effectuées de façon non-respect de la casse. Peut être ignoré par l’objet qui ne prend pas en charge la recherche de non-respect de la casse.|  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une des valeurs suivantes :  
  
|||  
|-|-|  
|`S_OK`|Opération réussie.|  
|`S_FALSE`|Membre existe mais ne peut pas être supprimé.|  
  
## <a name="remarks"></a>Notes  
 Si le membre est supprimé, le DISPID doit rester valide pour `GetNextDispID`.  
  
 Si un membre avec un nom donné est supprimé et recréé ultérieurement un membre portant le même nom, le DISPID doit être le même. (Si les membres qui diffèrent uniquement par la casse sont « même » est dépendant d’objets).  
  
## <a name="example"></a>Exemple  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)