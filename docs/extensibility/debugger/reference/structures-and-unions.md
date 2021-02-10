---
title: Structures et unions | Microsoft Docs
description: Cet article contient des liens vers des descriptions de référence des structures et des unions dans le kit de développement logiciel (SDK) de débogage Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6b055446e6bdf147c99cf96b48c03bfcfdd2eda2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938692"
---
# <a name="structures-and-unions"></a>Structures et unions
Voici les structures et les unions du kit de développement logiciel (SDK) de débogage Visual Studio.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Spécifie l’ID de processus, qui peut être un ID système ou un GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Décrit les conditions dans lesquelles un point d’arrêt est déclenché.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Décrit la résolution d’un point d’arrêt d’erreur, y compris l’emplacement, le programme et le thread.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Spécifie le type de structure utilisé pour décrire l’emplacement du point d’arrêt.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Définit les composants qui décrivent l’emplacement d’un point d’arrêt à une adresse dans le code.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Décrit l’emplacement d’un point d’arrêt qui est lié directement à une adresse dans le programme en cours de débogage.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Décrit l’emplacement d’un point d’arrêt à la ligne d’un fichier source de code.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Décrit l’emplacement de décalage d’un point d’arrêt au niveau d’une fonction dans le code.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Utilisé pour définir des points d’arrêt de code basés sur une chaîne que l’utilisateur peut entrer à partir de l’IDE.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Utilisé pour définir des points d’arrêt sur variable basés sur une chaîne que l’utilisateur peut entrer à partir de l’IDE.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Décrit la résolution d’un point d’arrêt à un emplacement spécifique.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Décrit le nombre et les conditions sur lesquelles un point d’arrêt doit être déclenché après avoir été passé précédemment.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Contient les informations requises pour implémenter un point d’arrêt.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Contient les informations requises pour implémenter un point d’arrêt (identique à la structure [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , mais inclut des informations sur le GUID, la contrainte et le point de trace du fournisseur).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Décrit l’emplacement d’un point d’arrêt de code.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Décrit le résultat de la liaison d’un point d’arrêt de données.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Décrit les informations de point d’arrêt lié pour un point d’arrêt de code ou de données.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Spécifie la structure de l’emplacement de résolution de point d’arrêt.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Décrit un tableau de chaînes.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Spécifie des informations sur un type de champ extrait des métadonnées.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Décrit un appel à une fonction ou à une méthode.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Décrit l’ordinateur sur lequel le débogueur s’exécute.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) Décrit une liste de GUID.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Décrit un contexte de mémoire ou un contexte de code.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Décrit une adresse dans un programme en cours de débogage.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Représente l’un des différents types d’adresses.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Identifie une visionneuse personnalisée ou un visualiseur de type.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Décrit une propriété de débogage qui, à son tour, décrit un objet d’une nature hiérarchique qui a le nom, le type et la valeur.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Décrit une référence.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Décrit le désassemblage dans l’IDE pour l’affichage.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Décrit une exception ou une erreur d’exécution levée par le programme en cours de débogage.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Décrit une variable locale, un paramètre ou un autre champ.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Décrit un frame de pile.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Décrit un tableau d’identificateurs uniques pour les moteurs de débogage disponibles.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Utilisé pour définir les informations de JustMyCode d’un module.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Décrit un ordinateur particulier.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Décrit un élément de tableau dans un tableau.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Décrit l’adresse d’un champ d’une classe ou d’une structure.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Décrit l’adresse d’une variable locale dans une portée (généralement une fonction ou une méthode).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Décrit l’adresse d’une méthode d’une classe.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Décrit un paramètre d’une méthode ou d’une fonction.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Décrit une valeur de retour d’une méthode ou d’une fonction.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Décrit un type de champ issu de métadonnées.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Décrit un module particulier (DLL, EXE ou assembly).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Décrit les informations d’État sur les chemins de recherche de symboles qui ont été recherchés.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Décrit une adresse native.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Décrit un type de champ issu d’un symbole PDB.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Décrit l’état d’un point d’arrêt qui est prêt à être lié à un emplacement de code.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Décrit un processus.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Décrit une liste d’objets [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représentent des nœuds de programme.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Décrit les processus qui s’exécutent sur un ordinateur.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Décrit l’emplacement de la ligne et de la colonne dans le texte donné.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) Décrit les propriétés d’un thread.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Décrit le type d’un champ.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Décrit une adresse physique.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Décrit une adresse relative à un `this` pointeur ( `Me` dans Visual Basic).

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h, SH. h ou EE. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Référence sur l’API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
