---
title: "IDebugErrorEvent2::GetErrorMessage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
helpviewer_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne les informations qui permettent la construction d'un message d'erreur explicite.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```c#  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### Paramètres  
 `pMessageType`  
 \[out\]  Retourne une valeur de l'énumération de [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) , qui décrit le type de message.  
  
 `pbstrErrorFormat`  
 \[out\]  Le format du message final à l'utilisateur \(consultez « notes » pour plus de détails\).  
  
 `hrErrorReason`  
 \[out\]  Code d'erreur le message est sur.  
  
 `pdwType`  
 \[out\]  Gravité de l'erreur \(utilisez des constantes de MB\_XXX pour `MessageBox`; par exemple, `MB_EXCLAMATION` ou `MB_WARNING`\).  
  
 `pbstrHelpFileName`  
 \[out\]  Chemin d'accès à un fichier d'aide \(a une valeur NULL s'il n'existe aucun fichier d'aide\).  
  
 `pdwHelpId`  
 \[out\]  ID de la rubrique d'aide à afficher \(la valeur 0 s'il n'existe aucune rubrique d'aide\).  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Le message d'erreur doit être mises en forme le long de les lignes d' `"What I was doing.  %1"`.  `"%1"` serait alors remplacé par l'appelant avec le message d'erreur dérivé de code d'erreur \(qui est retourné dans `hrErrorReason`\).  Le paramètre d' `pMessageType` indique à l'appelant que le message d'erreur final doit s'afficher.  
  
## Voir aussi  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)