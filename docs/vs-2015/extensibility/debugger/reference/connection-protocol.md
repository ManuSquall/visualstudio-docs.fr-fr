---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 72ed9b8a747814d9537739c8dc27e5f113547756
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62561852"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Indique le protocole utilisé pour la communication entre un serveur de débogage et le package DE débogage (DE).  
  
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
 Aucune connexion n’a été établie à un serveur.  
  
 CONNECTION_UNKNOWN  
 Une connexion a été établie, mais son type est inconnu.  
  
 CONNECTION_LOCAL  
 Connexion à un serveur local.  
  
 CONNECTION_PIPE  
 La connexion s’effectue via un canal nommé.  
  
 CONNECTION_TCPIP  
 La connexion utilise TCP/IP.  
  
 CONNECTION_HTTP  
 La connexion utilise HTTP (via un serveur Web).  
  
 CONNECTION_OTHER  
 Un autre type de connexion a été établi (cette valeur n’est pas utilisée actuellement).  
  
## <a name="remarks"></a>Notes  
 Ces valeurs sont retournées à partir de la méthode [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) .  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
