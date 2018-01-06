---
title: CompilandDetails | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: CompilandDetails symbol
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cc892cbdf49ab883c2bd45f4ef13ddda21b23d83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="compilanddetails"></a>CompilandDetails
Informations de compiland sont partagées entre les symboles avec un `SymTagCompiland` balise (détail faible) et un `SymTagCompilandDetails` balise (détail haute). `SymTagCompilandDetails`requiert le chargement de symboles supplémentaires. Toutefois, il fournit une multitude d’informations sur le module qui n’est pas disponible avec un `SymTagCompiland` symbole.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant présente les propriétés qui sont valides pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Numéro de build de back-end du compilateur.|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Numéro de version majeure du back-end du compilateur.|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Numéro de version mineure du back-end du compilateur.|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nom du compilateur qui a généré ce compiland (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE`Si Modifier & Continuer sont activé au niveau de la compilation.|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Numéro de build front-end du compilateur.|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Numéro de version majeure front-end du compilateur.|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Numéro de version mineure frontale du compilateur.|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE`Si cette compiland comporte des informations de débogage (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE`Si cette compiland contient du code managé (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE`Si le module a été compilé avec le [/GS (vérification de la sécurité de la mémoire tampon)](/cpp/build/reference/gs-buffer-security-check) commutateur du compilateur (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE`Si compiland a été convertie à partir du code de langage CIL (Common Intermediate) en code natif.|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE`Si les types définis par l’utilisateur (UDT) ont été alignés à certaines spécifiées limite de mémoire (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE`Si le module a été compilé avec le [/hotpatch (créer une Image corrigeable en mémoire)](/cpp/build/reference/hotpatch-create-hotpatchable-image) commutateur du compilateur (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE`Si le module a été compilé avec le [/LTCG (génération de Code d’édition de liens)](/cpp/build/reference/ltcg-link-time-code-generation) commutateur du compilateur (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE si le module est un module de langage MSIL (Microsoft Intermediate) (uniquement dans DIA SDK 8.0 ou version ultérieure).|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Langage de code source.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbole du module.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID de symbole lexicale parente.|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plateforme sur laquelle le module a été compilé (parmi les [cv_cpu_type_e, énumération](../../debugger/debug-interface-access/cv-cpu-type-e.md) valeurs).|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index du symbole.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagCompilandDetails` (parmi les [symtagenum, énumération](../../debugger/debug-interface-access/symtagenum.md) valeurs).|  
  
## <a name="remarks"></a>Notes  
 Les compilateurs utilisent souvent dans un formulaire appelé un compilateur deux passes ; dans certaines versions du compilateur, chaque passe est géré par un autre programme. Ils sont appelés des compilateurs frontaux et principaux, respectivement, par conséquent, les symboles de propriété pour les numéros de version principale et frontale.  
  
## <a name="see-also"></a>Voir aussi  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)