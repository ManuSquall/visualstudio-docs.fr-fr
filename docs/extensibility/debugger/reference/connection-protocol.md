---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d09d751dd51306810f4d0cbb56d701859e2b183
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036470"
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
Indique le protocole utilisé pour communiquer entre un serveur de débogage et le package de débogage (dé).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum tagCONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
} CONNECTION_PROTOCOL;  
```  
  
```csharp  
public enum CONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 CONNECTION_NONE  
 Aucune connexion n’a été effectuée sur un serveur.  
  
 CONNECTION_UNKNOWN  
 Une connexion a été établie, mais il s’agit d’un type inconnu.  
  
 CONNECTION_LOCAL  
 Est de la connexion à un serveur local.  
  
 CONNECTION_PIPE  
 La connexion est via un canal nommé.  
  
 CONNECTION_TCPIP  
 Connexion utilise le protocole TCP/IP.  
  
 CONNECTION_HTTP  
 Connexion utilise le protocole HTTP (via un serveur Web).  
  
 CONNECTION_OTHER  
 Un autre type de connexion a été établie (cette valeur n’est pas actuellement utilisée).  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont retournées à partir de la [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)