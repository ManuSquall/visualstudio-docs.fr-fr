---
title: Structures et Unions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0ef171d24b3744657a2cb05338b2b124a6331c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864672"
---
# <a name="structures-and-unions"></a>Structures et unions
Voici les structures et unions dans le SDK de débogage de Visual Studio.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Spécifie l’ID de processus, ce qui peut être un ID système ou un GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) décrit les conditions sous lesquelles un point d’arrêt se déclenche.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) décrit la résolution d’un point d’arrêt erreur, y compris l’emplacement, de programme et de thread.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Spécifie le type de structure utilisée pour décrire l’emplacement du point d’arrêt.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) définit les composants qui décrivent l’emplacement d’un point d’arrêt à une adresse dans le code.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) décrit l’emplacement d’un point d’arrêt est directement lié à une adresse dans le programme en cours de débogage.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) décrit l’emplacement d’un point d’arrêt à la ligne dans un fichier de code source.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) décrit l’emplacement de décalage d’un point d’arrêt à une fonction dans le code.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) utilisée pour définir des points d’arrêt de code basés sur une chaîne que l’utilisateur peut entrer à partir de l’IDE.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) utilisée pour définir des points d’arrêt de données qui sont basées sur une chaîne de l’utilisateur peut entrer à partir de l’IDE.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) décrit la résolution d’un point d’arrêt à un emplacement spécifique.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) décrit le nombre et les conditions sur lequel un point d’arrêt est déclenché après avoir été précédemment passée.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) contient les informations requises pour implémenter un point d’arrêt.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) contient les informations requises pour implémenter un point d’arrêt (identique à la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) structure mais il inclut les informations de GUID, de contrainte et de point de trace du fournisseur).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) décrit l’emplacement d’un point d’arrêt du code.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) décrit le résultat de la liaison d’un point d’arrêt de données.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) décrit les informations de point d’arrêt lié pour un point d’arrêt de code ou un point d’arrêt de données.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) spécifie la structure de l’emplacement de la résolution de point d’arrêt.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) décrit un tableau de chaînes.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) spécifie des informations sur un type de champ extraites à partir des métadonnées.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) décrit un appel à une fonction ou méthode.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) décrit l’ordinateur sur lequel le débogueur est en cours d’exécution.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) décrit une liste de GUID.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) décrit un contexte de la mémoire ou d’un contexte de code.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) décrit une adresse dans un programme en cours de débogage.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) représente un d’un nombre de différents types d’adresses.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) identifie une visionneuse personnalisée ou visualiseur de type.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) décrit une propriété de débogage qui à son tour décrit un objet de nature hiérarchique qui a le nom, type et valeur.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) décrit une référence.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) décrit le code machine à l’IDE pour l’affichage.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) décrit une erreur d’exécution ou d’exception levée par le programme en cours de débogage.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) décrit une variable locale, paramètre ou un autre champ.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) décrit un frame de pile.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) décrit un tableau d’identificateurs uniques pour les moteurs de débogage disponibles.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) utilisé pour définir les informations JustMyCode pour un module.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) décrit un ordinateur particulier.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) décrit un élément de tableau dans un tableau.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) décrit l’adresse d’un champ d’une classe ou structure.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) décrit l’adresse d’une variable locale dans une étendue (généralement une fonction ou méthode).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) décrit l’adresse d’une méthode d’une classe.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) décrit un paramètre d’une méthode ou une fonction.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) décrit une valeur de retour à partir d’une méthode ou une fonction.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) décrit un type de champ extraites à partir des métadonnées.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) décrit un module particulier (EXE, DLL ou assembly).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) décrit les informations d’état sur les chemins de recherche de symbole qui a été effectuée dans.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) décrit une adresse native.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) décrit un type de champ extraites à partir d’un symbole PDB.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) décrit l’état d’un point d’arrêt est prêt à lier à un emplacement de code.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) décrit un processus.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) décrit la liste des [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objets qui représentent des nœuds de programme.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) décrit le processus qui s’exécutent sur un ordinateur.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) décrit l’emplacement de colonne et de ligne dans le texte donné.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) décrit les propriétés d’un thread.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) décrit un type de champ.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) décrit une adresse physique.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) décrit une adresse qui est relative à un `this` pointeur (`Me` en Visual Basic).

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h, sh.h ou ee.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur les API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)