---
title: SymTagEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 806fe878468baa06b52a15879ceaff1b376461e9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738513"
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
`SymTagNull` indique que le symbole n’a pas de type.

`SymTagExe` indique que le symbole est un fichier. exe. Il n’existe qu’un seul symbole `SymTagExe` par magasin de symboles. Il sert d’étendue globale et n’a pas de parent lexical.

`SymTagCompiland` indique le symbole de module de la base de code pour chaque composant du magasin de symboles. Pour les applications natives, `SymTagCompiland` symboles correspondent aux fichiers objets liés à l’image. Pour certains types d’images MSIL (Microsoft Intermediate Language), il existe un seul compiland par classe.

`SymTagCompilandDetails` indique que le symbole contient des attributs étendus du compiland. La récupération de ces propriétés peut nécessiter le chargement de symboles compiland.

`SymTagCompilandEnv` indique que le symbole est une chaîne d’environnement définie pour le compiland.

`SymTagFunction` indique que le symbole est une fonction.

`SymTagBlock` indique que le symbole est un bloc imbriqué.

`SymTagData` indique que le symbole est une donnée.

`SymTagAnnotation` indique que le symbole est destiné à une annotation de code. Les enfants de ce symbole sont des chaînes de données constantes (`SymTagData`, `LocIsConstant`, `DataIsConstant`). La plupart des clients ignorent ce symbole.

`SymTagLabel` indique que le symbole est une étiquette.

`SymTagPublicSymbol` indique que le symbole est un symbole public. Pour les applications natives, ce symbole est le symbole externe COFF rencontré lors de la liaison de l’image.

`SymTagUDT` indique que le symbole est un type défini par l’utilisateur (structure, classe ou Union).

`SymTagEnum` indique que le symbole est une énumération.

`SymTagFunctionType` indique que le symbole est un type de signature de fonction.

`SymTagPointerType` indique que le symbole est un type pointeur.

`SymTagArrayType` indique que le symbole est un type tableau.

`SymTagBaseType` indique que le symbole est un type de base.

`SymTagTypedef` indique que le symbole est un `typedef`, autrement dit un alias pour un autre type.

`SymTagBaseClass` indique que le symbole est une classe de base d’un type défini par l’utilisateur.

`SymTagFriend` indique que le symbole est un Friend d’un type défini par l’utilisateur.

`SymTagFunctionArgType` indique que le symbole est un argument de fonction.

`SymTagFuncDebugStart` indique que le symbole est l’emplacement de fin du code de prologue de la fonction.

`SymTagFuncDebugEnd` indique que le symbole est l’emplacement de début du code épilogue de la fonction.

`SymTagUsingNamespace` indique que le symbole est un nom d’espace de noms, actif dans l’étendue actuelle.

`SymTagVTableShape` indique que le symbole est une description de la table virtuelle.

`SymTagVTable` indique que le symbole est un pointeur de table virtuelle.

`SymTagCustom` indique que le symbole est un symbole personnalisé et n’est pas interprété par DIA.

`SymTagThunk` indique que le symbole est un thunk utilisé pour partager des données entre 16 et 32 bits de code.

`SymTagCustomType` indique que le symbole est un symbole de compilateur personnalisé.

`SymTagManagedType` indique que le symbole est dans les métadonnées.

`SymTagDimension` indique que le symbole est un tableau multidimensionnel FORTRAN.

`SymTagCallSite` indique que le symbole représente le site d’appel.

`SymTagInlineSite` indique que le symbole représente le site en ligne.

`SymTagBaseInterface` indique que le symbole est une interface de base.

`SymTagVectorType` indique que le symbole est un type de vecteur.

`SymTagMatrixType` indique que le symbole est un type de matrice.

`SymTagHLSLType` indique que le symbole est un type de langage de nuanceur de haut niveau.

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

## <a name="requirements"></a>spécifications
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
