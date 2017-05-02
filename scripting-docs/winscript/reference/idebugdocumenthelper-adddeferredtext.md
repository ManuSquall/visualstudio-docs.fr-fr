---
title: "IDebugDocumentHelper::AddDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddDeferredText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddDeferredText"
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddDeferredText
Demande au programme d'assistance que le texte spécifié est disponible, mais il ne fournit pas de caractères.  
  
## Syntaxe  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### Paramètres  
 `cChars`  
 \[in\]  Nombre de caractères \(Unicode\) à ajouter.  
  
 `dwTextStartCookie`  
 \[in\]  cookie hôte défini qui représente la position de départ du texte.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|La méthode a échoué.|  
  
## Notes  
 Cette méthode permet à l'hôte de différer fournir les caractères pour ajouter jusqu'à ce qu'ils soient nécessaires, tout en permettant au programme d'assistance pour générer des notifications exactes et les informations de taille.  Le paramètre d' `dwTextStartCookie` est un cookie, défini par l'hôte, qui représente la position de départ du texte.  Les appels suivants à `IDebugDocumentText::GetText` doivent fournir ce cookie.  Par exemple, dans un hôte qui représente le texte dans DBCS, le cookie peut être un décalage d'octet.  
  
 On suppose qu'un seul appel à `IDebugDocumentText::GetText` peut obtenir des caractères plusieurs appels à `AddDeferredText`.  Les classes d'assistance peuvent également indiquer le même plage de caractères différés plusieurs fois.  
  
> [!NOTE]
>  Les appels à `AddDeferredText` ne doivent pas être associés à des appels à `AddUnicodeText` ou à `AddDBCSText`.  Si cela se produit, `E_FAIL` est retourné.  
  
## Voir aussi  
 [IDebugDocumentHelper, interface](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)