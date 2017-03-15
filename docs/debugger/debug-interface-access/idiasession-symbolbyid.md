---
title: "IDiaSession::symbolById | Microsoft Docs"
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
  - "IDiaSession::symbolById (méthode)"
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSession::symbolById
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un symbole par son identificateur unique.  
  
## Syntaxe  
  
```cpp#  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### Paramètres  
 `id`  
 \[in\]  identificateur unique.  
  
 `ppSymbol`  
 \[out\]  Retourne un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le symbole extrait.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 L'identificateur spécifié est une valeur unique utilisée en interne par le diamètre Kit de développement logiciel pour rendre des symboles uniques.  
  
 Cette méthode peut être utilisée, par exemple, pour récupérer le symbole représentant le type d'autre symbole \(consultez l'exemple\).  
  
## Exemple  
 Cet exemple récupère [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) représentant le type d'autre symbole.  Cet exemple montre comment utiliser la méthode d' `symbolById` dans la session.  Une approche plus simple est d'appeler la méthode d' [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) pour récupérer le symbole de type directement.  
  
```cpp#  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## Voir aussi  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)