---
title: 'IDispatchEx :: GetNextDispID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8811e828a6701769badf45ca7c37f9c53529150f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144427"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID

Énumère les membres de l’objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetNextDispID(
   DWORD grfdex,
   DISPID id,
   DISPID *pid
);
```

## <a name="parameters"></a>Paramètres

`grfdex`\
Détermine l’ensemble d’éléments à énumérer. Il peut s’agir d’une combinaison des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|fdexEnumDefault|Demande que l’objet énumère les éléments par défaut. L’objet est autorisé à énumérer tout ensemble d’éléments.|
|fdexEnumAll|Demande que l’objet énumère tous les éléments. L’objet est autorisé à énumérer tout ensemble d’éléments.|

`id`\
Identifie le membre actuel. GetNextDispID récupère l’élément dans l’énumération après celui-ci. Utilise GetDispID ou un appel précédent à GetNextDispID pour obtenir cet identificateur. Utilise la valeur DISPID_STARTENUM pour obtenir le premier identificateur du premier élément.

`pid`\
Adresse d’une variable DISPID qui reçoit l’identificateur de l’élément suivant dans l’énumération.

Si un membre est supprimé par `DeleteMemberByName` ou `DeleteMemberByDispID` , le `DISPID` doit rester valide pour `GetNextDispID` .

## <a name="return-value"></a>Valeur de retour

Renvoie l'une des valeurs suivantes :

|Valeur|Signification|
|-|-|
|`S_OK`|Réussite.|
|`S_FALSE`|L’énumération est terminée.|

## <a name="example"></a>Exemple

```cpp
   HRESULT hr;
   BSTR bstrName;
   DISPID dispid;
   IDispatchEx *pdex;

   // Assign to pdex
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);
   while (hr == NOERROR)
   {
      hr = pdex->GetMemberName(dispid, &bstrName);
      if (!wcscmp(bstrName, OLESTR("Bar")))
      {
         SysFreeString(bstrName);
         return TRUE;
      }
      SysFreeString(bstrName);
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);
   }
```

## <a name="see-also"></a>Voir aussi

- [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)