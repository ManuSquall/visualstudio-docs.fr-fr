---
title: "IDebugDocumentText, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentText (interface)"
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText, interface
Permet d'accéder à une version texte uniquement du document de débogage.  Cette interface utilise les conventions suivantes :  
  
-   Les positions et les numéros de ligne d'impression sont de base zéro.  
  
-   Les Caractère\- positions représentent des offsets de caractères ; elles ne représentent pas les offsets d'octets ou de mot.  Pour Win32, une caractère\- position est Unicode est décalé.  
  
 Outre les méthodes héritées de `IDebugDocument`, l'interface `IDebugDocumentText` expose les méthodes suivantes.  
  
## Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Retourne les attributs du document.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Retourne le nombre de lignes et le nombre de caractères du document.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Caractère\- position de la valeur correspondant au premier caractère d'une ligne.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Retourne le numéro de ligne et, éventuellement, le décalage de caractère dans la ligne correspondant à la caractère\- position donnée.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Récupère les caractères et\/ou les attributs de caractère associés à un intervalle de caractère\- position.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Retourne la plage de caractère\- position correspondante dans un contexte de document.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Crée un objet de contexte de document qui correspond à la plage fourni de la position du caractère.|