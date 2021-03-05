---
description: Spécifie le type de symbole.
title: SymTagEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 72d07b0609fd9d66507c898854810043f2911e0c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161605"
---
# <a name="symtagenum"></a>SymTagEnum
Spécifie le type de symbole.

## <a name="syntax"></a>Syntaxe

```C++
enum SymTagEnum {
    SymTagNull,
    SymTagExe,
    SymTagCompiland,
    SymTagCompilandDetails,
    SymTagCompilandEnv,
    SymTagFunction,
    SymTagBlock,
    SymTagData,
    SymTagAnnotation,
    SymTagLabel,
    SymTagPublicSymbol,
    SymTagUDT,
    SymTagEnum,
    SymTagFunctionType,
    SymTagPointerType,
    SymTagArrayType,
    SymTagBaseType,
    SymTagTypedef,
    SymTagBaseClass,
    SymTagFriend,
    SymTagFunctionArgType,
    SymTagFuncDebugStart,
    SymTagFuncDebugEnd,
    SymTagUsingNamespace,
    SymTagVTableShape,
    SymTagVTable,
    SymTagCustom,
    SymTagThunk,
    SymTagCustomType,
    SymTagManagedType,
    SymTagDimension,
    SymTagCallSite,
    SymTagInlineSite,
    SymTagBaseInterface,
    SymTagVectorType,
    SymTagMatrixType,
    SymTagHLSLType
};
```

## <a name="elements"></a>Éléments
`SymTagNull` Indique que le symbole n’a pas de type.

`SymTagExe` Indique que le symbole est un fichier. exe. Il n’y a qu’un seul `SymTagExe` symbole par magasin de symboles. Il sert d’étendue globale et n’a pas de parent lexical.

`SymTagCompiland` Indique le symbole compiland pour chaque composant de module de base de code du magasin de symboles. Pour les applications natives, `SymTagCompiland` les symboles correspondent aux fichiers objets liés à l’image. Pour certains types d’images MSIL (Microsoft Intermediate Language), il existe un seul compiland par classe.

`SymTagCompilandDetails` Indique que le symbole contient des attributs étendus du compiland. La récupération de ces propriétés peut nécessiter le chargement de symboles compiland.

`SymTagCompilandEnv` Indique que le symbole est une chaîne d’environnement définie pour le compiland.

`SymTagFunction` Indique que le symbole est une fonction.

`SymTagBlock` Indique que le symbole est un bloc imbriqué.

`SymTagData` Indique que le symbole est de données.

`SymTagAnnotation` Indique que le symbole est destiné à une annotation de code. Les enfants de ce symbole sont des chaînes de données constantes ( `SymTagData` , `LocIsConstant` , `DataIsConstant` ). La plupart des clients ignorent ce symbole.

`SymTagLabel` Indique que le symbole est une étiquette.

`SymTagPublicSymbol` Indique que le symbole est un symbole public. Pour les applications natives, ce symbole est le symbole externe COFF rencontré lors de la liaison de l’image.

`SymTagUDT` Indique que le symbole est un type défini par l’utilisateur (structure, classe ou Union).

`SymTagEnum` Indique que le symbole est une énumération.

`SymTagFunctionType` Indique que le symbole est un type de signature de fonction.

`SymTagPointerType` Indique que le symbole est un type pointeur.

`SymTagArrayType` Indique que le symbole est un type tableau.

`SymTagBaseType` Indique que le symbole est un type de base.

`SymTagTypedef` Indique que le symbole est un `typedef` , autrement dit un alias pour un autre type.

`SymTagBaseClass` Indique que le symbole est une classe de base d’un type défini par l’utilisateur.

`SymTagFriend` Indique que le symbole est un Friend d’un type défini par l’utilisateur.

`SymTagFunctionArgType` Indique que le symbole est un argument de fonction.

`SymTagFuncDebugStart` Indique que le symbole est l’emplacement de fin du code de prologue de la fonction.

`SymTagFuncDebugEnd` Indique que le symbole est l’emplacement de début du code épilogue de la fonction.

`SymTagUsingNamespace` Indique que le symbole est un nom d’espace de noms, actif dans l’étendue actuelle.

`SymTagVTableShape` Indique que le symbole est une description de la table virtuelle.

`SymTagVTable` Indique que le symbole est un pointeur de table virtuelle.

`SymTagCustom` Indique que le symbole est un symbole personnalisé et qu’il n’est pas interprété par DIA.

`SymTagThunk` Indique que le symbole est un thunk utilisé pour partager des données entre 16 et 32 bits de code.

`SymTagCustomType` Indique que le symbole est un symbole de compilateur personnalisé.

`SymTagManagedType` Indique que le symbole est dans les métadonnées.

`SymTagDimension` Indique que le symbole est un tableau multidimensionnel FORTRAN.

`SymTagCallSite` Indique que le symbole représente le site d’appel.

`SymTagInlineSite` Indique que le symbole représente le site en ligne.

`SymTagBaseInterface` Indique que le symbole est une interface de base.

`SymTagVectorType` Indique que le symbole est un type de vecteur.

`SymTagMatrixType` Indique que le symbole est un type de matrice.

`SymTagHLSLType` Indique que le symbole est un type de langage de nuanceur de haut niveau.

## <a name="remarks"></a>Notes
Tous les symboles d’un fichier de débogage ont une balise d’identification qui spécifie le type du symbole.

Les valeurs de cette énumération sont retournées par un appel à la méthode [IDiaSymbol :: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) .

Les valeurs de cette énumération sont passées aux méthodes suivantes pour limiter l’étendue de la recherche à un type de symbole spécifique :

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Configuration requise
En-tête : cvconst. h

## <a name="see-also"></a>Voir aussi
- [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
