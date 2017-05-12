---
title: "IActiveScriptParse | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParse (interface)"
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse
Si le moteur de Script Windows permet aux scriptlets de code de texte brut à ajouter au script ou permet le texte d'expression à évaluer au moment de l'exécution, elle implémente l'interface d' `IActiveScriptParse` .  Pour les langages de script interprètes qui n'ont aucun environnement de création indépendant, tel que VBScript, cela offre un autre mécanisme \(autre que `IPersist*`\) pour déplacer le code de script dans le moteur de script, et pour joindre des fragments de script à différents événements d'objet.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Initialise le moteur de script.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Ajoute un scriptlet de code au script.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analyse le scriptlet donné de code, ajoutez les déclarations dans l'espace de noms et évaluant le code en conséquence.|  
  
## Voir aussi  
 [Script actif, interfaces](../../winscript/reference/active-script-interfaces.md)