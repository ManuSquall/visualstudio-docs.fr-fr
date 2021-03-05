---
description: Représente un fournisseur de symboles COM+ avec des méthodes qui sont spécifiques au code managé.
title: IDebugComPlusSymbolProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 20ede060901a9aeec591fb17d1f632cb5d228963
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163471"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Représente un fournisseur de symboles COM+ avec des méthodes qui sont spécifiques au code managé.

## <a name="syntax"></a>Syntaxe

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Bien qu’il n’existe pas de séparation entre les interfaces qui sont utiles à un évaluateur d’expression (EE) et celles qui sont destinées à être utilisées par un moteur DE débogage (DE), les méthodes suivantes peuvent probablement intéresser les développeurs uniquement : AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols et UpdateSymbols.

## <a name="methods"></a>Méthodes
 Outre les méthodes sur l’interface [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) , cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Détermine si les symboles de débogage sont chargés pour le module spécifié en fonction de l’identificateur de domaine d’application.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Crée un type à partir du type primitif spécifié.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Mappe une position de document dans le module spécifié à un tableau d’adresses de débogage.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Récupère des informations de type sur le tableau spécifié en fonction de son adresse de débogage.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Récupère le nom de l’assembly en fonction de son module et de son domaine d’application.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Récupère les classes avec l’attribut spécifié qui sont implémentées dans le langage de programmation donné.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Récupère les classes avec l’attribut spécifié dans un module donné.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Récupère le point d’entrée de l’application.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Récupère l’adresse dans une fonction qui représente l’offset de ligne donné.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Récupère la disposition des variables locales pour un ensemble de méthodes.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Retourne le nom associé au jeton spécifié en fonction de son objet de métadonnées.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Récupère les symboles de débogage avec l’attribut parent donné pour le module spécifié.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Récupère le lecteur de symboles à utiliser par le code non managé.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Récupère un type de symbole en fonction de son adresse de débogage.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Détermine si la fonction à l’adresse de débogage spécifiée est supprimée.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Détermine si la fonction à l’adresse de débogage spécifiée est considérée comme obsolète.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Détermine si le code à l’adresse de débogueur spécifiée est masqué.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Charge les symboles de débogage spécifiés en mémoire.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Charge les symboles de débogage en fonction du flux de données.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Remplace les symboles de débogage actuels par ceux du flux de données spécifié.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Décharge les symboles de débogage pour le module spécifié à partir de la mémoire.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Met à jour les symboles de débogage dans la mémoire avec ceux du flux de données spécifié.|

## <a name="requirements"></a>Configuration requise
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
