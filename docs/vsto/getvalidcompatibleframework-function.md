---
title: "GetValidCompatibleFramework, fonction | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: dfb365c0-5ffc-4290-ab8b-bd347e0f0db9
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# GetValidCompatibleFramework, fonction
  Ce les prend en charge l'infrastructure d'API Office et n'est pas destinées à être utilisés directement à partir de votre code.  
  
## Syntaxe  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|N'utilisez pas.|  
|*pbstrValidFrameworkTag*|N'utilisez pas.|  
  
## Valeur de retour  
 Si la fonction réussit, elle retourne **S\_OK**.  Si la fonction échoue, elle retourne un code d'erreur.  
  
  