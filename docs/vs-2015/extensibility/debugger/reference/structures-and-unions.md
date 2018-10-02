---
title: Structures et Unions | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6c4a5b371d52a249dafd4b13844e3ef3c6c5dff3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47492924"
---
# <a name="structures-and-unions"></a>Structures et unions
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Structures et Unions](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/structures-and-unions).  
  
Voici les structures et unions dans le SDK de débogage de Visual Studio.  
  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 Spécifie l’ID de processus, ce qui peut être un ID système ou un GUID.  
  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Décrit les conditions sous lesquelles un point d’arrêt se déclenche.  
  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 Décrit la résolution d’un point d’arrêt erreur, y compris l’emplacement, de programme et de thread.  
  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 Spécifie le type de structure utilisée pour décrire l’emplacement du point d’arrêt.  
  
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Définit les composants qui décrivent l’emplacement d’un point d’arrêt à une adresse dans le code.  
  
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Décrit l’emplacement d’un point d’arrêt est directement lié à une adresse dans le programme en cours de débogage.  
  
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 Décrit l’emplacement d’un point d’arrêt à la ligne dans un fichier de code source.  
  
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Décrit l’emplacement de décalage d’un point d’arrêt à une fonction dans le code.  
  
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Utilisée pour définir des points d’arrêt de code basés sur une chaîne que l’utilisateur peut entrer à partir de l’IDE.  
  
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Utilisée pour définir des points d’arrêt de données qui sont basées sur une chaîne de l’utilisateur peut entrer à partir de l’IDE.  
  
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 Décrit la résolution d’un point d’arrêt à un emplacement spécifique.  
  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Décrit le nombre et les conditions sur lequel un point d’arrêt est déclenché après avoir été précédemment passée.  
  
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Contient les informations requises pour implémenter un point d’arrêt.  
  
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Contient les informations requises pour implémenter un point d’arrêt (identique à la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) structure mais il inclut les informations de GUID, de contrainte et de point de trace du fournisseur).  
  
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 Décrit l’emplacement d’un point d’arrêt du code.  
  
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Décrit le résultat de la liaison d’un point d’arrêt de données.  
  
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Décrit les informations de point d’arrêt lié pour un point d’arrêt de code ou un point d’arrêt de données.  
  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 Spécifie la structure de l’emplacement de la résolution de point d’arrêt.  
  
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 Décrit un tableau de chaînes.  
  
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 Spécifie les informations relatives à un type de champ pris à partir des métadonnées.  
  
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Décrit un appel à une fonction ou méthode.  
  
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 Décrit l’ordinateur sur lequel le débogueur est en cours d’exécution.  
  
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Décrit une liste de GUID.  
  
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)  
 Décrit un contexte de la mémoire ou d’un contexte de code.  
  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Décrit une adresse dans un programme en cours de débogage.  
  
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Représente un d’un nombre de différents types d’adresses.  
  
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 Identifie une visionneuse personnalisée ou type de visualiseur.  
  
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Décrit une propriété de débogage qui à son tour décrit un objet de nature hiérarchique qui a le nom, type et valeur.  
  
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 Décrit une référence.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 Décrit le code machine à l’IDE pour l’affichage.  
  
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Décrit une exception ou une erreur d’exécution levées par le programme en cours de débogage.  
  
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Décrit une variable locale, paramètre ou un autre champ.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 Décrit un frame de pile.  
  
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 Décrit un tableau d’identificateurs uniques pour les moteurs de débogage disponibles.  
  
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 Utilisé pour définir les informations JustMyCode pour un module.  
  
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 Décrit un ordinateur particulier.  
  
 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Décrit un élément de tableau dans un tableau.  
  
 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 Décrit l’adresse d’un champ d’une classe ou structure.  
  
 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Décrit l’adresse d’une variable locale dans une étendue (généralement une fonction ou méthode).  
  
 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 Décrit l’adresse d’une méthode d’une classe.  
  
 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Décrit un paramètre d’une méthode ou une fonction.  
  
 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 Décrit une valeur de retour à partir d’une méthode ou une fonction.  
  
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 Décrit un type de champ extraites à partir des métadonnées.  
  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)  
 Décrit un module particulier (EXE, DLL ou assembly).  
  
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 Décrit les informations d’état sur les chemins de recherche de symbole qui a été effectuée dans.  
  
 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 Décrit une adresse native.  
  
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Décrit un type de champ pris à partir d’un symbole PDB.  
  
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Décrit l’état d’un point d’arrêt est prêt à lier à un emplacement de code.  
  
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)  
 Décrit un processus.  
  
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 Décrit la liste des [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objets qui représentent des nœuds de programme.  
  
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 Décrit les processus qui s’exécutent sur un ordinateur.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 Décrit l’emplacement de colonne et de ligne dans le texte donné.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 Décrit les propriétés d’un thread.  
  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
 Décrit un type de champ.  
  
 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 Décrit une adresse physique.  
  
 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Décrit une adresse qui est relative à un `this` pointeur (`Me` en Visual Basic).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h, sh.h ou ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)

