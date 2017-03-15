---
title: "IDebugProcess2::GetAttachedSessionName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetAttachedSessionName"
helpviewer_keywords: 
  - "IDebugProcess2::GetAttachedSessionName"
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProcess2::GetAttachedSessionName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le nom de la session qui sont traduits dans ce processus.  L'IDE peut afficher ces informations pour l'utilisateur qui sont traduits dans un processus particulier sur un ordinateur particulier.  
  
> [!NOTE]
>  Cette méthode est déconseillée, et son implémentation doit toujours retourner `E_NOTIMPL`.  
  
## Syntaxe  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### Paramètres  
 `pbstrSessionName`  
  
## Valeur de retour  
 Cette méthode doit toujours retourner `E_NOTIMPL`.  
  
## Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)