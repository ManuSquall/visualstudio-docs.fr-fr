---
title: "IActiveScriptAuthor::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetScriptTextAttributes"
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetScriptTextAttributes
Retourne les attributs de texte pour un bloc de script.  
  
## Syntaxe  
  
```  
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### Paramètres  
 `pszCode`  
 \[dans, size\_is \(`cch`\)\] le texte du bloc de script.  Cette chaîne ne doit pas être null terminée.  
  
 `cch`  
 \[in\]  la taille utilisée pour les paramètres d' `pszCode` et d' `pattr` .  
  
 `pszDelimiter`  
 \[in\]  L'adresse du délimiteur de fin de script.  Lorsque `pszCode` est analysé d'un flux de texte, l'hôte utilise généralement un séparateur \(par exemple deux guillemets simples\), pour détecter la fin du scriptlet.  Définissez ce paramètre POUR ANNULER s'il n'existe aucun séparateur pour identifier la fin du bloc de script.  
  
 `dwFlags`  
 \[in\]  Les balises associées à des attributs de texte du bloc de script.  Peut être une combinaison des valeurs suivantes :  
  
|Constante|Valeur|Description|  
|---------------|------------|-----------------|  
|GETATTRTYPE\_DEPSCAN|0x0001|Identifiez les identificateurs comportant l'attribut de SOURCETEXT\_ATTR\_IDENTIFIER, et identifiez les opérateurs de débogage avec l'attribut de SOURCETEXT\_ATTR\_MEMBERLOOKUP.|  
|GETATTRFLAG\_THIS|0x0100|Identifiez l'objet actif qui a l'attribut de SOURCETEXT\_ATTR\_THIS.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|Identifiez le contenu de la chaîne et supprimez le texte qui a l'attribut de SOURCETEXT\_ATTR\_HUMANTEXT.|  
  
 `pattr`  
 \[dans, size\_is \(`cch`\)\] Les informations sur la couleur du code de bloc de script.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IActiveScriptAuthor, interface](../../winscript/reference/iactivescriptauthor-interface.md)   
 [SOURCE\_TEXT\_ATTR, énumération](../../winscript/reference/source-text-attr-enumeration.md)