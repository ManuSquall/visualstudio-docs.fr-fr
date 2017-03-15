---
title: "MESSAGETYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MESSAGETYPE"
helpviewer_keywords: 
  - "Énumération MESSAGETYPE"
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MESSAGETYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

spécifie le type de message et la raison.  
  
## Syntaxe  
  
```cpp#  
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
  
```c#  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## Membres  
 MT\_OUTPUTSTRING  
 Indique que le message doit être envoyé à la fenêtre Sortie.  Cela s'excluent mutuellement d' `MT_MESSAGEBOX`.  
  
 MT\_MESSAGEBOX  
 Indique que le message doit être affiché dans un message.  Cela s'excluent mutuellement d' `MT_OUTPUTSTRING`.  
  
 MT\_TYPE\_MASK  
 une valeur de masque pour isoler la destination pour le message.  
  
 MT\_REASON\_EXCEPTION  
 Indique qu'un message s'affiche à la suite d'une exception.  Cela s'excluent mutuellement d' `MT_REASON_TRACEPOINT`.  
  
 MT\_REASON\_TRACEPOINT  
 Indique qu'un message s'affiche à la suite de atteindre un point de trace.  Cela s'excluent mutuellement à `MT_REASON_EXCEPTION`.  
  
 MT\_REASON\_MASK  
 Une valeur de masque pour isoler la raison du message indiqué.  
  
## Notes  
 Ces valeurs sont retournées par les méthodes d' [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) et d' [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) .  
  
 L'une des valeurs de raison peut être combiné avec une des valeurs de destination de sortie avec l' `OR`de bits.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)