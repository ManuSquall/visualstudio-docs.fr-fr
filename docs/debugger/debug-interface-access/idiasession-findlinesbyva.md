---
title: "IDiaSession::findLinesByVA | Microsoft Docs"
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
  - "IDiaSession::findLinesByVA (méthode)"
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::findLinesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Extrait les informations de numéro de ligne pour les lignes contenues dans une plage spécifiée \(VA\) d'adresse virtuelle.  
  
## Syntaxe  
  
```cpp#  
HRESULT findLinesByVA (   
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Paramètres  
 `va`  
 \[in\]  spécifie l'adresse comme VA.  
  
 `length`  
 \[in\]  spécifie le nombre d'octets de plage d'adresses pour couvrir de cette requête.  
  
 `ppResult`  
 \[out\]  Retourne un objet d' [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) qui contient une liste de tous les numéros de ligne qui décrivent la plage d'adresse spécifiée.  
  
## Exemple  
 Cet exemple illustre une fonction qui obtient tous les numéros de ligne contenus dans une fonction à l'aide de l'adresse virtuelle et la longueur de la fonction.  
  
```cpp#  
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    ULONGLONG            va;  
    ULONGLONG            length;  
  
    if (pFunc->get_virtualAddress ( &va ) == S_OK)  
    {  
        pFunc->get_length( &length );  
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## Voir aussi  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)