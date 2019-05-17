---
title: IDispatchEx::DeleteMemberByName | Microsoft Docs
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
ms.openlocfilehash: dc7c8db4ab28e0bd0fcb48f352cb07595f72fd17
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000888"
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