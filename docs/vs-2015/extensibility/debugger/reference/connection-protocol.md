---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f59c551e335d013f6fb004ece1f6a107a5b8de33
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508155"
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CONNECTION_PROTOCOL](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/connection-protocol).  
  
Indique le protocole utilisé pour communiquer entre un serveur de débogage et le package de débogage (dé).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum tagCONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
} CONNECTION_PROTOCOL;  
```  
  
```csharp  
public enum CONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)

