---
title: CompilandDetails | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 56ed4b317dc9259458ddb9f984c5d086595d7846
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033919"
---
# <a name="compilanddetails"></a>CompilandDetails
Informations de compiland sont réparties entre les symboles avec un `SymTagCompiland` balise (détail faible) et un `SymTagCompilandDetails` balise (beaucoup de détails). `SymTagCompilandDetails` nécessite le chargement de symboles supplémentaires. Toutefois, il fournit une mine d’informations sur le module qui n’est pas disponible avec un `SymTagCompiland` symbole.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant présente les propriétés qui sont valides pour ce type de symbole.  
  
|Property|Type de données|Description|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Numéro de build de back-end du compilateur.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Numéro de version principale de back-end du compilateur.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Numéro de version secondaire de back-end du compilateur.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nom du compilateur qui a généré cette compiland (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` Si Modifier & Continuer a été activé à la compilation.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Numéro de build frontal du compilateur.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Numéro de version principale frontal du compilateur.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Numéro de version mineure frontal du compilateur.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` Si cette compiland a des informations de débogage (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` Si cette compiland contient du code managé (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` Si le module a été compilé avec le [/GS (vérification de la sécurité de la mémoire tampon)](/cpp/build/reference/gs-buffer-security-check) commutateur de compilateur (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` Si compiland a été converti à partir du code de langage CIL (Common Intermediate) en code natif.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` Si les types définis par l’utilisateur (UDT) ont été alignées sur certaines spécifiées des limites de mémoire (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` Si compiland a été compilé avec le [/hotpatch (créer une Image corrigeable en mémoire)](/cpp/build/reference/hotpatch-create-hotpatchable-image) commutateur de compilateur (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` Si compiland a été compilé avec le [/LTCG (Link-time Code Generation)](/cpp/build/reference/ltcg-link-time-code-generation) commutateur de compilateur (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE si compiland est un module de langage MSIL (Microsoft Intermediate Language) (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Langage de code source.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole du module.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID du symbole lexicale parente.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plateforme sur laquelle le module a été compilé (parmi les [CV_CPU_TYPE_e (énumération)](../../debugger/debug-interface-access/cv-cpu-type-e.md) valeurs).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index de symbole.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagCompilandDetails` (parmi les [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md) valeurs).|  
  
## <a name="remarks"></a>Notes  
 Les compilateurs utilisent souvent dans un formulaire appelé un compilateur deux passes ; dans certaines versions du compilateur, chaque passage est gérée par un programme distinct. Ceux-ci sont connus comme les compilateurs frontaux et principaux, respectivement, par conséquent, les symboles de propriété pour les numéros de version principal et frontal.  
  
## <a name="see-also"></a>Voir aussi  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)