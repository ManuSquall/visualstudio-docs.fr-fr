---
title: "IDiaSession::findLinesByLinenum | Microsoft Docs"
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
  - "IDiaSession::findLinesByLinenum (méthode)"
ms.assetid: 76d5622d-9a91-4c2a-a98f-263af5d1daef
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findLinesByLinenum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Détermine les numéros de ligne du module \(compiland\) que le numéro de ligne spécifié dans un fichier source se trouve dans ou approche.  
  
## Syntaxe  
  
```cpp#  
HRESULT findLinesByLinenum (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Paramètres  
 `compiland`  
 \[in\]  Un objet d' [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le module dans lequel vous pouvez rechercher les numéros de ligne.  Ce paramètre ne peut pas être `NULL`.  
  
 `file`  
 \[in\]  Un objet d' [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) qui représente le fichier source pour le rechercher dans.  Ce paramètre ne peut pas être `NULL`.  
  
 `linenum`  
 \[in\]  spécifie un numéro de ligne de base 1.  
  
> [!NOTE]
>  Vous ne pouvez pas utiliser zéro pour spécifier toutes les lignes \(utilisez la méthode d' [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md) pour rechercher toutes les lignes\).  
  
 `column`  
 \[in\]  spécifie le numéro de colonne.  utilisation zéro de spécifier toutes les colonnes.  Une colonne est un offset d'octets en une ligne.  
  
 `ppResult`  
 \[out\]  Retourne un objta d' [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) qui contient une liste des numéros de ligne récupérés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
 L'exemple suivant montre comment ouvrir un fichier source, énumérer les paramètres fournis par ce fichier, et rechercher les numéros de ligne dans le fichier source où commence de chaque module \(compiland\).  
  
```cpp#  
void ShowLinesInCompilands(IDiaSession *pSession, LPCOLESTR filename)  
{  
    IDiaEnumSourceFiles* pEnum;  
    IDiaSourceFile*      pFile;  
    DWORD                celt;  
  
    pSession->findFile ( NULL, filename, nsFNameExt, &pEnum );  
    while ( pEnum->Next ( 1, &pFile, &celt ) == S_OK ) // for each file  
    {  
        IDiaEnumSymbols* pEnumCompilands;  
        IDiaSymbol* pCompiland;  
  
        pFile->get_compilands ( &pEnumCompilands );  
        // for each compiland  
        while ( pEnumCompilands->Next ( 1, &pCompiland, &celt ) == S_OK )  
        {  
            IDiaEnumLineNumbers* pEnum;  
            // Find first compiland closest to line 1 of the file.  
            if (pSession->findLinesByLinenum( pCompiland, pFile, 1, 0, &pEnum ) == S_OK)  
            {  
                IDiaLineNumber *pLineNumber;  
                DWORD lineCount;  
                while ( pEnum->Next(1,&pLineNumber,&lineCount) == S_OK)  
                {  
                     DWORD lineNum;  
                     if (pLineNumber->get_line(&lineNum) == S_OK)  
                     {  
                          printf("compiland starts in source at line number = %lu\n",lineNum);  
                     }  
                }  
            }  
        }  
    }  
}  
```  
  
## Voir aussi  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)