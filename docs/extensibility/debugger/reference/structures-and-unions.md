---
title: Structures et syndicats (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19d8f547d98488edffc6049be7619e5b5e921d93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713492"
---
# <a name="structures-and-unions"></a>Structures et unions
Ce qui suit sont les structures et les syndicats dans le Visual Studio Debugging SDK.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Spécifie l’ID du processus, qui peut être soit une pièce d’identité système ou un GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Décrit les conditions dans lesquelles un point d’arrêt s’allumera.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Décrit la résolution d’un point d’erreur, y compris l’emplacement, le programme et le thread.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Spécifie le type de structure utilisée pour décrire l’emplacement du point d’arrêt.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Définit les composants qui décrivent l’emplacement d’un point d’arrêt à une adresse dans le code.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Décrit l’emplacement d’un point d’arrêt qui est lié directement à une adresse dans le programme étant débogé.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Décrit l’emplacement d’un point d’arrêt en ligne dans un fichier source de code.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Décrit l’emplacement décalé d’un point d’arrêt à une fonction dans le code.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Utilisé pour définir des points de rupture de code en fonction d’une chaîne que l’utilisateur peut entrer à partir de l’IDE.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Utilisé pour définir des points de rupture de données qui sont basés sur une chaîne que l’utilisateur peut entrer à partir de l’IDE.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Décrit la résolution d’un point d’arrêt à un endroit précis.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Décrit le nombre et les conditions sur lesquelles un point d’arrêt sera tiré après avoir été précédemment passé.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Contient les informations nécessaires à la mise en œuvre d’un point d’arrêt.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Contient les informations nécessaires à la mise en œuvre d’un point d’arrêt (même que la structure [BP_REQUEST_INFO,](../../../extensibility/debugger/reference/bp-request-info.md) mais comprend des informations de guiD, de contrainte et de tracepoint du fournisseur).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Décrit l’emplacement d’un point d’arrêt de code.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Décrit le résultat de la liaison d’un point d’arrêt des données.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Décrit les informations de point de rupture lié pour un point d’arrêt de code ou un point d’arrêt de données.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Spécifie la structure de l’emplacement de résolution du point de rupture.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Décrit un tableau de cordes.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Spécifie les informations sur un type de terrain tiré des métadonnées.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Décrit un appel à une fonction ou une méthode.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Décrit l’ordinateur sur lequel le débbuggeur est en marche.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) Décrit une liste de GUIDs.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Décrit un contexte de mémoire ou un contexte de code.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Décrit une adresse dans un programme en cours de débocisation.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Représente l’un des nombreux types d’adresses.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Identifie un visualiseur personnalisé ou un visualisateur de type.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Décrit une propriété de débocher qui décrit à son tour un objet de nature hiérarchique qui a le nom, le type et la valeur.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Décrit une référence.

- [DémontageData](../../../extensibility/debugger/reference/disassemblydata.md) Décrit le démontage à l’IDE pour l’affichage.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Décrit une erreur d’exception ou de temps d’exécution lancée par le programme étant débogé.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Décrit une variable, un paramètre ou un autre champ local.

- [FRAMEINFO (EN ANGLAIS)](../../../extensibility/debugger/reference/frameinfo.md) Décrit un cadre de pile.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Décrit une gamme d’identifiants uniques pour les moteurs de débogé disponibles.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Utilisé pour définir les informations JustMyCode pour un module.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Décrit une machine particulière.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Décrit un élément de tableau dans un tableau.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Décrit l’adresse d’un champ d’une classe ou d’une structure.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Décrit l’adresse d’une variable locale dans une portée (généralement une fonction ou une méthode).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Décrit l’adresse d’une méthode d’une classe.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Décrit un paramètre d’une méthode ou d’une fonction.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Décrit une valeur de retour à partir d’une méthode ou d’une fonction.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Décrit un type de champ tiré des métadonnées.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Décrit un module particulier (DLL, EXE ou assemblage).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Décrit les informations d’état sur les chemins de recherche des symboles qui ont été recherchés.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Décrit une adresse autochtone.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Décrit un type de champ tiré d’un symbole PDB.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Décrit l’état d’un point d’arrêt qui est prêt à se lier à un emplacement de code.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Décrit un processus.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Décrit une liste d’objets [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représentent les nœuds de programme.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Décrit les processus fonctionnant sur une machine.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Décrit l’emplacement de la ligne et de la colonne dans le texte donné.

- [THREADPROPERTIES (EN)](../../../extensibility/debugger/reference/threadproperties.md) Décrit les propriétés d’un thread.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Décrit le type d’un champ.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Décrit une adresse physique.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Décrit une adresse qui est `this` relative`Me` à un pointeur (dans Visual Basic).

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h, sh.h, ou ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Référence des API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
