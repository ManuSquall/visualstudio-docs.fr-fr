---
title: "IDebugProgramEx2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEx2::Attach"
helpviewer_keywords: 
  - "IDebugProgramEx2::Attach"
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Attachez \-vous à un programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### Paramètres  
 `pCallback`  
 \[in\]  Un objet d' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui représente la fonction de rappel que le moteur de débogage attaché envoie des événements.  
  
 `dwReason`  
 \[in\]  Une valeur de l'énumération d' [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) qui décrit la raison de l'opération d'attachement.  
  
 `pSession`  
 \[in\]  Une valeur qui identifie de façon unique la session qui s'attache au programme.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  Cette méthode doit retourner `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` si le programme est déjà attachée.  
  
## Notes  
 Le port qui contient le programme peut utiliser la valeur dans `pSession` pour déterminer la session tente de joindre au programme.  Par exemple, si un port permet une seule session de débogage de s'attacher à un processus à la fois, le port peut déterminer si la même session est déjà attachée à d'autres programmes dans le processus.  
  
> [!NOTE]
>  L'interface passée dans `pSession` doit être traitée uniquement comme un cookie, une valeur qui identifie le gestionnaire de débogage de session l'attachement à ce programme ; aucune des méthodes sur l'interface fournie n'est fonctionnelle.  
  
## Voir aussi  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)