---
title: "IDiaSession::getEnumTables | Microsoft Docs"
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
  - "IDiaSession::getEnumTables (méthode)"
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSession::getEnumTables
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Récupère un énumérateur pour tous les tables contenues dans le magasin de symboles.  
  
## Syntaxe  
  
```cpp#  
HRESULT getEnumTables (   
   IDiaEnumTables** ppEnumTables  
);  
```  
  
#### Paramètres  
 `ppEnumTables`  
 \[out\]  Retourne un objet d' [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) .  Utilisez cette interface pour énumérer les tables dans le magasin de symboles.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
 Cet exemple présente une fonction générale qui utilise la méthode de `getEnumTables` pour obtenir un objet énumérateur spécifique.  Si l'énumérateur est trouvé, la fonction retourne un pointeur qui peut être casté à l'interface souhaitée ; sinon, la fonction retourne `NULL`.  
  
```cpp#  
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)  
{  
    IUnknown *pUnknown = NULL;  
    if (pSession != NULL)  
    {  
        CComPtr<IDiaEnumTables> pEnumTables;  
        if (pSession->getEnumTables(&pEnumTables) == S_OK)  
        {  
             CComPtr<IDiaTable> pTable;  
             DWORD celt = 0;  
             while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&  
                   celt == 1)  
             {  
                  if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)  
                  {  
                       break;  
                  }  
                  pTable = NULL;  
             }  
        }  
    }  
    return(pUnknown);  
}  
```  
  
## Voir aussi  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)