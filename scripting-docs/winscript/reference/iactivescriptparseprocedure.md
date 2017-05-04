---
title: "IActiveScriptParseProcedure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptParseProcedure (interface)"
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure
Si le moteur de Script Windows permet le texte de code source pour les procédures sont ajoutées au script, il implémente l'interface d' `IActiveScriptParseProcedure` .  Pour les langages de script interprètes qui n'ont aucun environnement de création indépendant, tel que VBScript, cela offre un autre mécanisme \(autre que `IActiveScriptParse` ou `IPersist`\*\) pour ajouter des procédures de script à l'espace de noms.  
  
## Méthodes dans l'ordre Vtable  
  
|||  
|-|-|  
|Méthode|Description|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analyse la procédure de code donnée et ajoute la procédure à l'espace de noms.|  
  
## Voir aussi  
 [Script actif, interfaces](../../winscript/reference/active-script-interfaces.md)