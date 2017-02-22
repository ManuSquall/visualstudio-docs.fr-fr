---
title: "IDebugCoreServer3::EnableAutoAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
helpviewer_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Active l'attachement automatique pour les moteurs de débogage spécifiés.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```c#  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### Paramètres  
 `rgguidSpecificEngines`  
 \[in\]  Tableau de GUID pour chaque moteur de débogage marque comme automobile\-se attachement.  
  
 `celtSpecificEngines`  
 \[in\]  le nombre de moteurs spécifiés dans `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 \[in\]  L'URL commençant à utiliser automobile\-en attachement.  
  
 `pbstrSessionID`  
 \[out\]  ID de la session qui utilisent été jointe.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  Un code d'erreur est `E_AUTO_ATTACH_NOT_REGISTERED`, ce qui indique que la fabrique de classe d'auto\-attachement n'a pas été enregistrée.  
  
## Notes  
 Lorsqu'un programme associé à l'URL spécifiée est démarré, les moteurs de débogage spécifiés sont automatiquement démarrés et jointes.  
  
## Voir aussi  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)