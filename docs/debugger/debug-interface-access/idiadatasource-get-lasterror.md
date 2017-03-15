---
title: "IDiaDataSource::get_lastError | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaDataSource::get_lastError (méthode)"
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait le nom de fichier de la dernière erreur de chargement.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### Paramètres  
 pRetVal  
 \[out\]  Retourne une chaîne contenant le nom de fichier .pdb associé à la dernière erreur de chargement.  
  
## Valeur de retour  
 Retourne le dernier code d'erreur provoquée par une opération de chargement.  Retourne `E_INVALIDARG` si le paramètre d' `pRetVal` est `NULL`.  
  
## Exemple  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## Voir aussi  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)