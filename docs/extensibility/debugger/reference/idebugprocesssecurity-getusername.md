---
title: "IDebugProcessSecurity::GetUserName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::GetUserName"
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le nom d'utilisateur du fournisseur de port.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```c#  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### Paramètres  
 `pbstrUserName`  
 \[out\]  Chaîne contenant le nom d'utilisateur.  
  
## Valeur de retour  
 Si la méthode réussit, elle retourne `S_OK`.  Sinon il retourne un code d'erreur.  
  
## Notes  
 `GetUserName` retourne le nom d'utilisateur qui est affiché dans la colonne de **Nom d'utilisateur** de la boîte de dialogue d' **Attacher au processus** .  Pour afficher la boîte de dialogue d' **Attacher au processus** , cliquez sur **Attacher au processus** dans le menu d' **Outils** dans l'environnement de développement intégré \(IDE\) de \(IDE\) [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .  
  
## Voir aussi  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)