---
title: "SetWefProcessId, m&#233;thode | Microsoft Docs"
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
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# SetWefProcessId, m&#233;thode
  Fournit l'identificateur de processus qui exécute le contenu de l'infrastructure \(WEF\) d'extensions de site Web.  
  
## Syntaxe  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*dwProcessId*|l'identificateur de processus qui sera utilisé pour exécuter le contenu de WEF.|  
  
## Valeur de retour  
 Valeur HRESULT indiquant si la méthode s'est terminée correctement.  
  
## Notes  
 Cette méthode doit être appelée une fois le processus de contenu de WEF créé mais avant tout contenu de WEF s'exécute.  
  
 Si vous souhaitez l'environnement de développement pour attacher un débogueur au processus de contenu de WEF, l'environnement doit effectuer cette opération dans votre implémentation de cette méthode.  
  
  