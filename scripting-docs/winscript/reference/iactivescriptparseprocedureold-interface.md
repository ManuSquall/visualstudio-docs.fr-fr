---
title: "IActiveScriptParseProcedureOld, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld (interface)"
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptParseProcedureOld, interface
Permet le texte de code source pour les procédures sont ajoutées au script.  Pour les langages de script interprètes qui n'ont pas un environnement de création indépendant, tel que VBScript, cela offre un autre mécanisme \(autre que `IActiveScriptParse` ou `IPersist*`\) pour ajouter des procédures de script à l'espace de noms.  
  
> [!NOTE]
>  Cette interface est déconseillée en faveur de l'interface d' `IActiveScriptParseProcedure` .  
  
## Méthodes  
 Outre les méthodes héritées de `IUnknown`, l'interface `IActiveScriptParseProcedureOld` expose les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analyse la procédure de code donnée et ajoute la procédure à l'espace de noms.|  
  
## Voir aussi  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)