---
title: Exe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dll files
- Exe symbol
- .exe files
- executable files, Exe symbol
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 348edea779d22b6a7330712657740056e1bb766c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745212"
---
# <a name="exe"></a>Exe
Exe est le seul symbole sans un parent lexical ou de classe, car il représente la portée globale du fichier. exe ou. dll. Il n’y a qu’un seul symbole avec la balise `SymTagExe` par fichier. La méthode [IDiaSession :: get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md) retourne le symbole.

## <a name="properties"></a>Propriétés
 Le tableau suivant présente les propriétés qui sont valides pour ce type de symbole.

|Property|Type de données|Description|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|Âge de cet exécutable.|
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID` de cet exécutable.|
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE` si le fichier de symboles associé à cet exécutable contient des types C (uniquement dans DIA SDK v 8.0 ou version ultérieure).|
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE` si les symboles privés ont été supprimés du fichier de symboles associé à cet exécutable (uniquement dans DIA SDK v 8.0 ou version ultérieure).|
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|Valeur indiquant l’unité centrale cible (l’une des valeurs d' [énumération CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) ).|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nom du fichier. exe.|
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|Signature de l’exécutable.|
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|Chemin d’accès complet au fichier. pdb ou. dbg du fichier. exe.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index du symbole.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagExe` (l’une des valeurs d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) ).|

## <a name="see-also"></a>Voir aussi
- [IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)
- [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)