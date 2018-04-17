---
title: MESSAGETYPE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fa09d938e0e7c3853431369c7e0634242df2ee0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="messagetype"></a>MESSAGETYPE
Spécifie le type de message et la raison.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_MESSAGETYPE {   
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
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>Membres  
 MT_OUTPUTSTRING  
 Indique que le message doit être envoyé à la fenêtre Sortie. Cela s’excluent mutuellement `MT_MESSAGEBOX`.  
  
 MT_MESSAGEBOX  
 Indique que le message doit s’afficher dans une boîte de message. Cela s’excluent mutuellement `MT_OUTPUTSTRING`.  
  
 MT_TYPE_MASK  
 Une valeur de masque pour isoler la destination du message.  
  
 MT_REASON_EXCEPTION  
 Indique qu’une boîte de message est affichée à la suite d’une exception. Cela s’excluent mutuellement `MT_REASON_TRACEPOINT`.  
  
 MT_REASON_TRACEPOINT  
 Indique qu’une boîte de message est affichée à la suite d’un point de trace. Cela s’excluent mutuellement pour `MT_REASON_EXCEPTION`.  
  
 MT_REASON_MASK  
 Une valeur de masque pour isoler la raison pour le message affiché.  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont retournées à partir de la [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) et [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) méthodes.  
  
 Une des valeurs de la raison peut être combinée avec une des valeurs de destination de sortie à l’aide d’une opération de bits `OR`.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)