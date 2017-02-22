---
title: "Structures et Unions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "structures (Visual Studio SDK)"
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Structures et Unions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Voici les structures et les unions dans Visual Studio débogage du Kit de développement logiciel.  
  
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 Spécifie l'ID de processus, qui peut être un ID du système ou le GUID.  
  
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Décrit les conditions dans lesquelles un point d'arrêt le déclenche.  
  
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 décrit la résolution d'un point d'arrêt d'erreur, y compris l'emplacement, le programme, et le thread.  
  
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 spécifie le type de structure utilisé pour décrire l'emplacement du point d'arrêt.  
  
 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Définit les composants qui décrivent l'emplacement d'un point d'arrêt sur une adresse dans le code.  
  
 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Décrit l'emplacement d'un point d'arrêt qui est lié directement à une adresse dans le programme débogué.  
  
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 Décrit l'emplacement d'un point d'arrêt à la ligne dans un fichier source du code.  
  
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Décrit l'emplacement d'offset d'un point d'arrêt sur une fonction dans le code.  
  
 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Utilisé pour définir des points d'arrêt de code en fonction d'une chaîne que l'utilisateur peut entrer de l'IDE.  
  
 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Utilisé pour définir les points d'arrêt de données basées sur une chaîne que l'utilisateur peut entrer de l'IDE.  
  
 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 décrit la résolution d'un point d'arrêt à un emplacement spécifique.  
  
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Décrit le nombre et les conditions sur lesquels un point d'arrêt est après avoir été précédemment passé déclenché.  
  
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Contient des informations requises pour implémenter un point d'arrêt.  
  
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Contient des informations requises pour implémenter un point d'arrêt \(même que la structure de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) en incluant des informations de fournisseur GUID, de contrainte et de point de trace\).  
  
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 décrit l'emplacement d'un point d'arrêt de code.  
  
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Décrit le résultat de lier un point d'arrêt.  
  
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Décrit des informations liées de point d'arrêt pour un point d'arrêt de code ou un point d'arrêt.  
  
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 spécifie la structure de l'emplacement de résolution de point d'arrêt.  
  
 [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 Décrit un tableau de chaînes.  
  
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 spécifie des informations sur un type de champ pris des métadonnées.  
  
 [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Décrit un appel à une fonction ou une méthode.  
  
 [COMPUTER\_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 décrit l'ordinateur sur lequel le débogueur exécute.  
  
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Décrit une liste de GUID.  
  
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)  
 décrit un contexte ou un contexte de code de mémoire.  
  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Décrit une adresse dans un programme en cours de débogage.  
  
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Représente un d'un certain nombre de types d'adresses.  
  
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 identifie une visionneuse ou un visualiseur personnalisée de type.  
  
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Décrit une propriété de débogage qui décrit aussi un objet de nature hiérarchique avec le nom, le type, et la valeur.  
  
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 décrit une référence.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 Décrit le code machine à l'IDE pour l'affichage.  
  
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Décrit une exception ou une erreur d'exécution levée par le programme débogué.  
  
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Décrit une variable locale, le paramètre, ou un autre champ.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 décrit un frame de pile.  
  
 [GUID\_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 Décrit un tableau d'identificateurs uniques pour les moteurs de débogage disponibles.  
  
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 utilisé pour définir les informations de JustMyCode pour un module.  
  
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 décrit un ordinateur particulier.  
  
 [METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Décrit un élément de tableau dans un tableau.  
  
 [METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 décrit l'adresse d'un champ d'une classe ou d'une structure.  
  
 [METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Décrit l'adresse d'une variable locale dans une portée \(généralement une fonction ou une méthode\).  
  
 [METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 décrit l'adresse d'une méthode de classe.  
  
 [METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Décrit un paramètre d'une méthode ou fonction.  
  
 [METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 Décrit une valeur de retour d'une méthode ou fonction.  
  
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 décrit un type de champ pris des métadonnées.  
  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)  
 décrit un module particulier \(DLL, EXE, ou assembly\).  
  
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 Décrit des informations d'état sur les chemins de recherche de symboles qui ont été trouvés.  
  
 [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 décrit une adresse native.  
  
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Décrit un type de champ pris d'un symbole PDB.  
  
 [PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Décrit l'état d'un point d'arrêt qui est prêt à le lier à un emplacement du code.  
  
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)  
 décrit un processus.  
  
 [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 Décrit une liste d'objets d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représentent des nœuds de programme.  
  
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 Décrit les processus qui s'exécutent sur un ordinateur.  
  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 décrit l'emplacement de ligne et de colonne dans le texte donné.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 décrit les propriétés d'un thread.  
  
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)  
 décrit un type de champ.  
  
 [UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 décrit une adresse physique.  
  
 [UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Décrit une adresse qui est relatif à un pointeur d' `this` \(`Me` en Visual Basic\).  
  
## Configuration requise  
 en\-tête : msdbg.h, sh.h, ou ee.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Référence API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)