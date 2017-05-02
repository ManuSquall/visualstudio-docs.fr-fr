---
title: "IDebugDocumentHost::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetScriptTextAttributes"
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetScriptTextAttributes
Retourne les attributs de texte pour un bloc de texte du document.  
  
## Syntaxe  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### Paramètres  
 `pstrCode`  
 \[in\]  le texte de bloc de script.  Cette chaîne n'a pas besoin d'être null terminée.  
  
 `uNumCodeChars`  
 \[in\]  Le nombre de caractères du texte de bloc de script.  
  
 `pstrDelimiter`  
 \[in\]  adresse du séparateur d'END\-de\-script\-bloc.  Lorsque `pstrCode` est analysé d'un flux de texte, l'hôte utilise généralement un séparateur, par exemple deux guillemets simples \('\), pour détecter la fin du bloc de script.  Ce paramètre spécifie que le séparateur qui l'hôte utilisé, ce qui permet au moteur de script pour fournir du prétraitement primitive conditionnel \(par exemple, en remplaçant un guillemet simple \[« \] par deux guillemets simples pour l " utilisation comme séparateur\).  Exactement comment \(et\) si le moteur de script utilise ces informations dépendent du moteur de script.  Définissez ce paramètre POUR ANNULER si l'hôte n'avait pas l'habitude un séparateur pour marquer la fin du bloc de script.  
  
 `dwFlags`  
 \[in\]  Balises associées au bloc de script.  Peut être une combinaison de ces valeurs :  
  
|Constante|Valeur|Description|  
|---------------|------------|-----------------|  
|GETATTRTYPE\_DEPSCAN|0x0001|Indique que les identificateurs et les opérateurs de débogage doivent être marqués avec les indicateurs de SOURCETEXT\_ATTR\_IDENTIFIER et de SOURCETEXT\_ATTR\_MEMBERLOOKUP, respectivement.|  
|GETATTRFLAG\_THIS|0x0100|Indique que l'identificateur de l'objet actuel doit être marqué avec la balise de SOURCETEXT\_ATTR\_THIS.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|Indique que le contenu de la chaîne et le texte de commentaire doivent être marqués avec la balise de SOURCETEXT\_ATTR\_HUMANTEXT.|  
  
 `pattr`  
 \[in, out\]  mémoire tampon pour contenir les attributs retournés.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|L'hôte utilise uniquement des attributs par défaut.|  
  
## Notes  
 Cette méthode retourne les attributs de texte pour un bloc arbitraire de texte du document.  Il est acceptable que les hôtes retournent `E_NOTIMPL`, auquel cas les attributs par défaut sont utilisés.  
  
## Voir aussi  
 [IDebugDocumentHost, interface](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE\_TEXT\_ATTR, énumération](../../winscript/reference/source-text-attr-enumeration.md)