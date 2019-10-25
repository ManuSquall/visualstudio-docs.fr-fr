---
title: Fonction (kit de développement logiciel de debug interface Access) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Function symbol
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd901d1bb54f91042e0a8134f1f3cba6c29b396a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745125"
---
# <a name="function-debug-interface-access-sdk"></a>Fonction (Kit de développement logiciel de Debug Interface Access)
Chaque fonction est identifiée par un symbole de `SymTagFunction`.

## <a name="properties"></a>Propriétés
 Le tableau suivant présente les propriétés qui sont valides pour ce type de symbole.

|Property|`Data type`|Description|
|--------------|-----------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|L’une des valeurs de l' [énumération CV_access_e](../../debugger/debug-interface-access/cv-access-e.md), si la fonction est une fonction membre.|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Partie décalage de l’emplacement ; Pour plus d’informations, consultez l' [énumération LocationType (](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Partie section de l’emplacement ; Pour plus d’informations, consultez l' [énumération LocationType (](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Symbole de la classe, si la fonction est une fonction membre.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID du symbole parent de la classe.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` si la fonction est marquée en tant que constante.|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` si la fonction utilise une convention d’appel personnalisée (uniquement dans DIA SDK V 8.0 ou version ultérieure).|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` si la fonction effectue un retour Far (uniquement dans DIA SDK V 8.0 ou version ultérieure).|
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|`TRUE` si la fonction utilise la fonction de mémoire allouée (uniquement uinnder DIA SDK V 8.0 ou version ultérieure).|
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE` si la fonction contient C++la gestion des exceptions de style (uniquement dans le kit de développement logiciel (SDK) dia version 8.0 ou ultérieure).|
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|`TRUE` si la fonction contient une gestion asynchrone des exceptions (uniquement dans DIA SDK V 8.0 ou ultérieur).|
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE` si la fonction contient un assembly inline (uniquement dans DIA SDK V 8.0 ou version ultérieure).|
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE` si la fonction contient un appel [longjmp](/cpp/c-runtime-library/reference/longjmp) (uniquement dans dia SDK v 8.0 ou version ultérieure).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` si la fonction contient des contrôles de sécurité (uniquement dans DIA SDK V 8.0 ou ultérieur).|
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE` si la fonction contient une gestion structurée des exceptions de style Win32 (uniquement dans DIA SDK V 8.0 ou ultérieur).|
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE` si la fonction contient un appel [setjmp](/cpp/c-runtime-library/reference/setjmp) (uniquement dans dia SDK v 8.0 ou version ultérieure).|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` si la fonction a retourné une interruption (uniquement dans DIA SDK V 8.0 ou ultérieur).|
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE` si une fonction est virtuelle Intro.|
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE` si la fonction a été marquée avec l’un des attributs [inline,](/cpp/cpp/inline-functions-cpp) _ _ Inline, \__forceinline.|
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE` si la fonction est marquée avec l’attribut [Naked](/cpp/cpp/naked-cpp) (uniquement dans dia SDK v 8.0 ou version ultérieure).|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` si la fonction est statique (uniquement dans DIA SDK V 8.0 ou version ultérieure).|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Nombre d’octets du code de fonction, à partir de l’emplacement.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole du compiland englobant.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole parent lexical.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Les fonctions peuvent avoir des emplacements statiques ou de métadonnées ; Pour plus d’informations, consultez [emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nom de la fonction.|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` si la fonction n’est pas une fonction inline (uniquement n Kit de développement logiciel DIA version 8.0 ou ultérieure).|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` si la fonction n’est pas accessible (uniquement dans DIA SDK V 8.0 ou version ultérieure).|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` si la fonction ne retourne pas de valeur (uniquement dans DIA SDK V 8.0 ou version ultérieure).|
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|`TRUE` si la fonction a été compilée avec des vérifications de sécurité de tampon mais qu’aucun classement de pile n’a pu être effectué.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` si le code contient des informations de débogage pour le code optimisé (uniquement dans DIA SDK V 8.0 ou ultérieur).|
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE` si la fonction est virtuelle pure.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Position relative de cette fonction dans son module.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index du symbole.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagFunction` (l’une des valeurs d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Jeton de métadonnées pour la fonction.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbole de la signature de la fonction.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID du symbole de type.|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` si la fonction n’est pas alignée.|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|Forme non décorée du nom de la fonction (uniquement dans DIA SDK v 8.0 ou version ultérieure)|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Tout ou partie de la forme non décorée du nom de la fonction (uniquement dans le kit de développement logiciel (SDK) DIA version 8.0 ou ultérieure).|
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` si une fonction virtuelle.|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Position de cette fonction dans l’image exécutable.|
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Si une fonction virtuelle, le décalage dans la table de fonctions virtuelles.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` si la fonction est marquée comme volatile.|

## <a name="see-also"></a>Voir aussi
- [CV_access_e, énumération](../../debugger/debug-interface-access/cv-access-e.md)
- [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType, énumération](../../debugger/debug-interface-access/locationtype.md)
- [Emplacements des symboles](../../debugger/debug-interface-access/symbol-locations.md)