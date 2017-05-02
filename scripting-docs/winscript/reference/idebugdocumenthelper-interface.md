---
title: "IDebugDocumentHelper, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentHelper (interface)"
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper, interface
Fournissez des implémentations pour de nombreuses interfaces nécessaires pour l'hébergement BITS, tel qu' `IDebugDocument`, `IDebugDocumentContext`, `IDebugDocumentProvider`, `IDebugDocumentText`, et les interfaces d' `IDebugDocumentTextEvents` .  
  
 Outre les méthodes héritées de `IUnknown`, l'interface `IDebugDocumentHelper` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|Initialise un programme d'assistance de document de débogage avec un nom et d'origine.|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|Ajoute ce document à l'arborescence de documents.|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|Supprime ce document de l'arborescence de documents.|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|Ajoute une chaîne Unicode à la fin de ce document.|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|Ajoute une chaîne de caractères DBCS à la fin de ce document.|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|Définit `IDebugDocumentHost` pour ce document.|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|Demande au programme d'assistance que le texte spécifié est disponible, mais il ne fournit pas de caractères.|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|Signifie au programme d'assistance qu'une plage spécifique de caractères est un bloc de script exécuté par le moteur de script donné.|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|Définit les attributs par défaut à utiliser pour le texte qui n'est pas dans un bloc de script.|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|Définit les attributs sur une plage de texte.|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|Définit le nom long de le document.|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|Définit le nom court de le document.|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|Définit les attributs de ce document.|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|Retourne le nœud d'application de débogage correspondant à ce document.|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|Extrait la cuisinière des caractères et le moteur de script correspondant à un bloc de script.|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|Crée un débogage le contexte de document.|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|Apporte ce document vers le haut dans l'interface utilisateur du débogueur.|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|Apporte un contexte de ce document vers le haut dans l'interface utilisateur du débogueur.|