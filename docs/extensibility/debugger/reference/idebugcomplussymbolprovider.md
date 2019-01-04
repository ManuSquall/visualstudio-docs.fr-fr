---
title: IDebugComPlusSymbolProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 707cf44f6c4bff961df4225d23d8918ed4548e04
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948984"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Représente un fournisseur de symboles COM + avec des méthodes qui sont spécifiques au code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Bien qu’il n’existe pas de séparation entre les interfaces qui sont utiles à un évaluateur d’expression (EE) et celles qui sont destinées à être utilisées par un moteur de débogage (DE), les méthodes suivantes seront probablement probablement intéressé par les développeurs DE uniquement : AreSymbolsLoaded GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols et UpdateSymbols.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes sur le [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interface, cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Détermine si les symboles de débogage sont chargées pour le module spécifié, étant donné l’identificateur de domaine d’application.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Crée un type à partir du type primitif spécifié.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Mappe une position de document dans le module spécifié dans un tableau d’adresses de débogage.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Récupère les informations sur le tableau spécifié à partir de son adresse de débogage de type.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Récupère le nom de l’assembly en fonction de son domaine d’application et de module.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Récupère les classes avec l’attribut spécifié qui sont implémentées dans le langage de programmation donné.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Récupère les classes avec l’attribut spécifié dans un module donné.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Récupère le point d’entrée de l’application.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Récupère l’adresse d’une fonction qui représente l’offset de ligne donné.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Récupère la structure des variables locales pour un ensemble de méthodes.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Retourne le nom associé au jeton spécifié son objet de métadonnées spécifié.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Récupère les symboles de débogage avec l’attribut parent donné pour le module spécifié.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Récupère le lecteur de symboles à utiliser par le code non managé.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Extrait d’un type de symbole donné son adresse de débogage.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Détermine si la fonction à l’adresse de débogage spécifié est supprimée.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Détermine si la fonction à l’adresse de débogage spécifié est considérée comme obsolète.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Détermine si le code à l’adresse de débogueur spécifié est masqué.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Charge les symboles de débogage spécifié dans la mémoire.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Étant données le flux de données de symboles de débogage de charges.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Remplace les symboles de débogage actuelle avec ceux présents dans le flux de données spécifié.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Décharge les symboles de débogage pour le module spécifié de la mémoire.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Met à jour les symboles de débogage dans la mémoire avec celles du flux de données spécifié.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : SH.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll