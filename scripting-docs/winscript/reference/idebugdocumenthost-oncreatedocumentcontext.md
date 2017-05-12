---
title: "IDebugDocumentHost::OnCreateDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.OnCreateDocumentContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::OnCreateDocumentContext"
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::OnCreateDocumentContext
Avertit l'hôte qu'un nouveau contexte de document est créé et permet à l'hôte pour retourner éventuellement un inconnu de contrôle du nouveau contexte.  
  
## Syntaxe  
  
```  
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### Paramètres  
 `ppunkOuter`  
 \[out\]  un objet qui contrôle le nouveau contexte.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|L'hôte ne fournit pas d'objet de contrôle.|  
  
## Notes  
 Cette méthode permet à l'hôte pour ajouter la nouvelle fonctionnalité au programme d'assistance\- fournissait des contextes de document.  Cette méthode peut retourner **E\_NOTIMPL** ou un objet externe null dans ce cas, l'appelant est chargé de créer le contexte.  
  
## Voir aussi  
 [IDebugDocumentHost, interface](../../winscript/reference/idebugdocumenthost-interface.md)