---
title: IDebugErrorEvent2::GetErrorMessage - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ff1da2f2a2d24b958a613e6fe5cb58c0081ed3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730047"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Renvoie les informations qui permettent la construction d’un message d’erreur lisible par l’homme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>Paramètres
`pMessageType`\
[out] Renvoie une valeur de l’énumération [MESSAGETYPE,](../../../extensibility/debugger/reference/messagetype.md) décrivant le type de message.

`pbstrErrorFormat`\
[out] Le format du message final à l’utilisateur (voir "Remarques" pour plus de détails).

`hrErrorReason`\
[out] Le code d’erreur du message est d’environ.

`pdwType`\
[out] Sévérité de l’erreur (utiliser `MessageBox`les constantes MB_XXX pour ; par exemple, `MB_EXCLAMATION` ou `MB_WARNING`).

`pbstrHelpFileName`\
[out] Chemin vers un fichier d’aide (réglé à une valeur nulle s’il n’y a pas de fichier d’aide).

`pdwHelpId`\
[out] ID du sujet d’aide à afficher (réglé à 0 s’il n’y a pas de sujet d’aide).

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le message d’erreur doit être `"What I was doing.  %1"`formaté le long des lignes de . Le `"%1"` serait alors remplacé par l’appelant avec le message d’erreur `hrErrorReason`dérivé du code d’erreur (qui est retourné dans ). Le `pMessageType` paramètre indique à l’appelant comment le message d’erreur final doit être affiché.

## <a name="see-also"></a>Voir aussi
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [Messagetype](../../../extensibility/debugger/reference/messagetype.md)
