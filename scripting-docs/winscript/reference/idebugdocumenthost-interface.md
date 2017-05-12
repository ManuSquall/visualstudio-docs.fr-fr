---
title: "IDebugDocumentHost, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentHost (interface)"
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost, interface
Expose les fonctionnalités de l'hôte spécifique, telle que la coloration de syntaxe, le débogueur.  La méthode d' `IDebugDocumentHelper::SetDebugDocumentHost` prend cette interface en tant qu'argument.  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugDocumentHost` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Retourne une plage de caractères qui ont été ajoutés à l'aide de `IDebugDocumentHelper::AddDeferredText`, dans le document d'hôte d'origine.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Retourne les attributs de texte pour un bloc de texte du document.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Avertit l'hôte qu'un nouveau contexte de document est créé, et permet à l'hôte pour retourner éventuellement un objet qui contrôle le nouveau contexte.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Retourne le chemin d'accès complet \(nom de fichier\) du fichier source du document.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Retourne le nom du document, sans informations de chemin d'accès.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Avertit l'hôte que le fichier source du document a été enregistré et que son contenu doit être actualisé.|