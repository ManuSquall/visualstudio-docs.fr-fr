---
title: IDebugComPlusSymbolProvider - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 482ea1b2fb2eb7ddad46bd99694e4599e9fd9bbe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733477"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Représente un fournisseur de symboles COMMD avec des méthodes spécifiques au code géré.

## <a name="syntax"></a>Syntaxe

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Bien qu’il n’y ait pas de séparation entre les interfaces qui sont utiles à un évaluateur d’expression (EE) et ceux qui sont destinés à être utilisés par un moteur de débogé (DE), les méthodes suivantes intéresseront probablement les développeurs DE seulement: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols et UpdateSymbols.

## <a name="methods"></a>Méthodes
 En plus des méthodes de l’interface [IDebugSymbolProvider,](../../../extensibility/debugger/reference/idebugsymbolprovider.md) cette interface met en œuvre les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Détermine si les symboles de débogé sont chargés pour le module spécifié étant donné l’identifiant de domaine d’application.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Crée un type à partir du type primitif spécifié.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Cartographiez une position de document dans le module spécifié à un tableau d’adresses de débogé.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Récupère des informations de type sur le tableau spécifié compte tenu de son adresse de débogé.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Récupère le nom de l’assemblage compte tenu de son module et de son domaine d’application.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Récupère les classes avec l’attribut spécifié qui sont implémentées dans le langage de programmation donné.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Récupère les classes avec l’attribut spécifié dans un module donné.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Récupère le point d’entrée de l’application.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Récupère l’adresse dans une fonction qui représente le décalage de ligne donné.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Récupère la disposition des variables locales pour un ensemble de méthodes.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Retourne le nom associé au jeton spécifié compte tenu de son objet métadonnées.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Récupère les symboles de débogé avec l’attribut parent donné pour le module spécifié.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Récupère le lecteur de symbole pour être utilisé par le code non menté.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Récupère à un type de symbole donné son adresse de débaillement.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Détermine si la fonction à l’adresse de débogé spécifiée est supprimée.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Détermine si la fonction à l’adresse de débaille spécifiée est considérée comme périmée.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Détermine si le code à l’adresse de débagrément spécifiée est caché.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Charge les symboles de déboise spécifiés dans la mémoire.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Les charges déboisent les symboles donnés au flux de données.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Remplace les symboles de déboçons actuels par ceux du flux de données spécifié.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Décharge les symboles de déboise pour le module spécifié de mémoire.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Mise à jour des symboles de débogé dans la mémoire avec ceux du flux de données spécifiés.|

## <a name="requirements"></a>Spécifications
 En-tête: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
