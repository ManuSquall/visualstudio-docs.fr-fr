---
title: MESSAGETYPE (EN ANGLAIS) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4d0fd12495a59427500c16ef6f37d9f8b6e61f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714503"
---
# <a name="messagetype"></a>MESSAGETYPE
Spécifie le type de message et la raison.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
typedef DWORD MESSAGETYPE;
```

```csharp
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="fields"></a>Champs
 `MT_OUTPUTSTRING`\
 Indique que le message doit être envoyé à la fenêtre de sortie. C’est mutuellement `MT_MESSAGEBOX`exclusif de .

 `MT_MESSAGEBOX`\
 Indique que le message doit être affiché dans une boîte de message. C’est mutuellement `MT_OUTPUTSTRING`exclusif de .

 `MT_TYPE_MASK`\
 Une valeur de masque pour isoler la destination du message.

 `MT_REASON_EXCEPTION`\
 Indique qu’une boîte de message est affichée à la suite d’une exception. C’est mutuellement `MT_REASON_TRACEPOINT`exclusif de .

 `MT_REASON_TRACEPOINT`\
 Indique qu’une boîte de message est affichée à la suite de la frappe d’un point de trace. Cela s’exclut `MT_REASON_EXCEPTION`mutuellement de .

 `MT_REASON_MASK`\
 Une valeur de masque pour isoler la raison du message montré.

## <a name="remarks"></a>Notes
 Ces valeurs sont revenues des méthodes [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) et [GetErrorMessage.](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)

 L’une des valeurs de raison peut être combinée avec `OR`l’une des valeurs de destination de sortie en utilisant un peu plus.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
