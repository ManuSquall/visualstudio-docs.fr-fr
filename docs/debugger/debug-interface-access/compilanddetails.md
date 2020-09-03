---
title: CompilandDetails | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da102a8968bc3e29091f6b4b58ee6ef78c6c3fb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462252"
---
# <a name="compilanddetails"></a>CompilandDetails
Les informations de compiland sont réparties entre les symboles à l’aide d’une `SymTagCompiland` balise (faible détail) et d’une `SymTagCompilandDetails` balise (très détaillée). `SymTagCompilandDetails` fournit une multitude d’informations sur le module (compiland) qui n’est pas disponible avec un `SymTagCompiland` symbole.

## <a name="properties"></a>Propriétés
 Le tableau suivant présente les propriétés qui sont valides pour ce type de symbole.

|Propriété|Type de données|Description|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Numéro de build du serveur principal du compilateur.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Numéro de version principale principale du compilateur.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Numéro de version mineure principale du compilateur.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nom du compilateur qui a produit ce compiland (uniquement dans DIA SDK V 8.0 ou ultérieur).|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Si modifier & continuer a été activé lors de la compilation.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Numéro de build frontal du compilateur.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Numéro de version principale frontale du compilateur.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Numéro de version mineure frontale du compilateur.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Si ce module (compiland) contient des informations de débogage (uniquement dans DIA SDK V 8.0 ou version ultérieure).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Si ce module (compiland) contient du code managé (uniquement dans DIA SDK v 8.0 ou version ultérieure).|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Si le compiland a été compilé avec le commutateur du compilateur [/GS (vérification de la sécurité de la mémoire tampon)](/cpp/build/reference/gs-buffer-security-check) (uniquement dans dia SDK v 8.0 ou version ultérieure).|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Si le module compiland a été converti du code Common Intermediate Language (CIL) en code natif.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Si les types définis par l’utilisateur (UDT) ont été alignés sur des limites de mémoire spécifiées (uniquement dans DIA SDK V 8.0 ou version ultérieure).|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Si le module compiland a été compilé avec le commutateur de compilateur [/hotpatch (créer une image corrigeable en mémoire)](/cpp/build/reference/hotpatch-create-hotpatchable-image) (uniquement dans dia SDK v 8.0 ou version ultérieure).|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Si le module de connexion au module a été compilé avec le commutateur de compilateur [/LTCG (Linking Code Generation)](/cpp/build/reference/ltcg-link-time-code-generation) (uniquement dans dia SDK v 8.0 ou version ultérieure).|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE si le module compiland est un module MSIL (Microsoft Intermediate Language) (uniquement dans DIA SDK v 8.0 ou version ultérieure).|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Langage de code source.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole du compiland.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole parent lexical.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plateforme sur laquelle le compiland a été compilé (l’une des CV_CPU_TYPE_e valeurs d' [énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md) ).|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index du symbole.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagCompilandDetails` (l’une des valeurs d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) ).|

## <a name="remarks"></a>Notes
 Les compilateurs sont souvent sous une forme connue sous le nom de compilateur à deux passements. dans certaines versions du compilateur, chaque passe est gérée par un programme distinct. Il s’agit, respectivement, de compilateurs frontaux et principaux, des propriétés de symbole pour les numéros de version back-end et frontaux.

## <a name="see-also"></a>Voir aussi
- [Compiland](../../debugger/debug-interface-access/compiland.md)
- [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)