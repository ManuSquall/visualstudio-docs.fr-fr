---
title: IDiaSession::findLinesByLinenum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByLinenum method
ms.assetid: 76d5622d-9a91-4c2a-a98f-263af5d1daef
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2486d3cbbecad1dee6b171f105d155d95a4e231
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855129"
---
# <a name="idiasessionfindlinesbylinenum"></a>IDiaSession::findLinesByLinenum
Détermine les numéros de ligne du module de journalisation que le numéro de ligne spécifié dans un fichier source se trouve à l’intérieur ou à proximité.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findLinesByLinenum ( 
    IDiaSymbol*           compiland,
    IDiaSourceFile*       file,
    DWORD                 linenum,
    DWORD                 column,
    IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Paramètres
`compiland`

dans Objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le compiland dans lequel rechercher les numéros de ligne. Ce paramètre ne peut pas être `NULL`.

`file`

dans Objet [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) qui représente le fichier source dans lequel effectuer la recherche. Ce paramètre ne peut pas être `NULL`.

`linenum`

dans Spécifie un numéro de ligne de base un.

> [!NOTE]
> Vous ne pouvez pas utiliser la valeur zéro pour spécifier toutes les lignes (utilisez la méthode [IDiaSession :: findLines](../../debugger/debug-interface-access/idiasession-findlines.md) pour rechercher toutes les lignes).

`column`

dans Spécifie le numéro de colonne. Utilisez zéro pour spécifier toutes les colonnes. Une colonne est un décalage d’octet dans une ligne.

`ppResult`

à Retourne un objta [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) qui contient une liste des numéros de ligne récupérés.

## <a name="return-value"></a>Valeur de retour
En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="example"></a>Exemple
L’exemple suivant montre comment ouvrir un fichier source, énumérer le compilands fourni par ce fichier et localiser les numéros de ligne dans le fichier source où chaque compiland démarre.

```C++
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

## <a name="see-also"></a>Voir aussi
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
