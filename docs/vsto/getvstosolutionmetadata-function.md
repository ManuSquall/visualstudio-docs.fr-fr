---
title: "GetVstoSolutionMetadata, fonction | Microsoft Docs"
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
ms.assetid: e8195838-fb9f-42b2-bb76-7ae3753f7751
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# GetVstoSolutionMetadata, fonction
  Ce les prend en charge l'infrastructure d'API Office et n'est pas destinées à être utilisés directement à partir de votre code.  
  
## Syntaxe  
  
```  
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
#### Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*lpwszSolutionMetadataKey*|N'utilisez pas.|  
|*ppSolutionInfo*|N'utilisez pas.|  
  
## Valeur de retour  
 Si la fonction réussit, elle retourne **S\_OK**.  Si la fonction échoue, elle retourne un code d'erreur.  
  
  