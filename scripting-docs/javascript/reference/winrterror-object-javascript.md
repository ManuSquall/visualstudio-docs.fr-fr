---
title: "WinRTError, objet (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, WinRTError (objet)"
  - "WinRTError (objet) (JavaScript)"
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# WinRTError, objet (JavaScript)
Quand un appel Windows Runtime retourne un HRESULT qui indique une erreur, JavaScript la convertit en erreur Windows Runtime spécifique.  Il est disponible uniquement dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], quand le Windows Runtime est disponible, dans l'espace de noms JavaScript globale.  
  
## Syntaxe  
  
```  
  
errorObj = new WinRTError();   
```  
  
## Notes  
 Le type d'erreur WinRTError est utilisé uniquement pour les erreurs qui proviennent des API Windows Runtime.  
  
## Exemple  
 L'exemple suivant montre comment WinRTError est levé et intercepté.  
  
```javascript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## Méthodes  
 L'objet WinRTError n'a pas de méthode.  
  
## Propriétés  
 L'objet WinRTError a les mêmes propriétés que l'objet [Error, objet](../../javascript/reference/error-object-javascript.md).  
  
## Configuration requise  
 L'objet WinRTError est pris en charge uniquement dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], et n'est pas pris en charge dans Internet Explorer.  
  
## Voir aussi  
 [Error, objet](../../javascript/reference/error-object-javascript.md)