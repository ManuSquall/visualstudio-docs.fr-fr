---
title: "GetAutoInsertExtensions, m&#233;thode"
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
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# GetAutoInsertExtensions, m&#233;thode
  Obtient des informations sur les applications pour Office qui doivent être insérées automatiquement pendant le débogage.  
  
 Cette méthode est réservée à une utilisation ultérieure.  
  
## Syntaxe  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*psaExtensionNames*|Les noms d'extension des applications pour Office.|  
  
## Valeur de retour  
 Valeur HRESULT indiquant si la méthode s'est terminée correctement.  
  
## Notes  
 Chaque application pour qu'Office est inséré est retournée comme nom d'extension d'application Office, qui correspond à une valeur sous HKEY\_CURRENT\_USER \\Software\\Microsoft\\Office\\WEF\\Developer.  L'hôte doit rechercher ces valeurs dans le Registre et insérer automatiquement les extensions.  
  
  