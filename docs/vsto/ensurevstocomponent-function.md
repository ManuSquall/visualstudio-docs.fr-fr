---
title: "EnsureVSTOComponent, fonction"
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
ms.assetid: e101fcd5-37a2-4b8c-b9ac-a84624298736
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# EnsureVSTOComponent, fonction
  Ce les prend en charge l'infrastructure d'API Office et n'est pas destinées à être utilisés directement à partir de votre code.  
  
## Syntaxe  
  
```  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*pProject*|N'utilisez pas.|  
  
## Valeur de retour  
 Si la fonction réussit, elle retourne **S\_OK**.  Si la fonction échoue, elle retourne un code d'erreur.  
  
  