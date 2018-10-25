---
title: MESSAGETYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc81ac400ce2a94674a97d9b987bf1a3e7843105
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845423"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spécifie le type de message et le motif.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 Indique que le message doit être envoyé à la fenêtre de sortie. Cela s’excluent mutuellement `MT_MESSAGEBOX`.  
  
 MT_MESSAGEBOX  
 Indique que le message doit s’afficher dans une boîte de message. Cela s’excluent mutuellement `MT_OUTPUTSTRING`.  
  
 MT_TYPE_MASK  
 Une valeur de masque pour isoler la destination du message.  
  
 MT_REASON_EXCEPTION  
 Indique qu’une boîte de message est affichée à la suite d’une exception. Cela s’excluent mutuellement `MT_REASON_TRACEPOINT`.  
  
 MT_REASON_TRACEPOINT  
 Indique qu’une boîte de message est affichée à la suite d’un point de trace. Cela est mutuellement exclusif avec `MT_REASON_EXCEPTION`.  
  
 MT_REASON_MASK  
 Une valeur de masque pour isoler la raison pour le message affiché.  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont retournées à partir de la [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) et [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) méthodes.  
  
 Une des valeurs de raison peut être combinée avec une des valeurs de destination de sortie à l’aide d’une opération de bits `OR`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)

