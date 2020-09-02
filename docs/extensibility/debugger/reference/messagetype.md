---
title: MESSAGETYPE | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
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
 Indique que le message doit être envoyé à la fenêtre sortie. Cela s’exclut mutuellement de `MT_MESSAGEBOX` .

 `MT_MESSAGEBOX`\
 Indique que le message doit s’afficher dans une boîte de message. Cela s’exclut mutuellement de `MT_OUTPUTSTRING` .

 `MT_TYPE_MASK`\
 Valeur de masque pour isoler la destination du message.

 `MT_REASON_EXCEPTION`\
 Indique qu’une boîte de message est affichée à la suite d’une exception. Cela s’exclut mutuellement de `MT_REASON_TRACEPOINT` .

 `MT_REASON_TRACEPOINT`\
 Indique qu’une boîte de message est affichée à la suite de l’atteinte d’un trace. Cela s’exclut mutuellement de `MT_REASON_EXCEPTION` .

 `MT_REASON_MASK`\
 Valeur de masque pour isoler la raison pour laquelle le message est affiché.

## <a name="remarks"></a>Notes
 Ces valeurs sont retournées à partir des méthodes [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) et [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) .

 L’une des raisons possibles peut être combinée avec l’une des valeurs de destination de sortie à l’aide d’une opération de bits `OR` .

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
