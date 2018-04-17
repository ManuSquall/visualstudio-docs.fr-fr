---
title: IDebugComPlusSymbolProvider | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1eab7e30715032500719ee371011a600d2e9552
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Représente un fournisseur de symbole COM + avec des méthodes qui sont spécifiques au code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Bien qu’il n’existe pas de séparation entre les interfaces qui sont utiles pour l’évaluateur d’expression (EE) et ceux qui sont destinés à être utilisés par un moteur de débogage (DE), les méthodes suivantes vous intéressent probablement aux développeurs DE uniquement : AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols et UpdateSymbols.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes sur le [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interface, cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Détermine si les symboles de débogage sont chargées pour le module spécifié, étant donné l’identificateur de domaine d’application.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Crée un type à partir du type primitif spécifié.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Mappe une position de document dans le module spécifié dans un tableau d’adresses de débogage.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Récupère les informations sur le tableau spécifié, étant donné son adresse de débogage de type.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Récupère le nom de l’assembly en fonction de son domaine d’application et de module.|  
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Récupère les classes avec l’attribut spécifié qui sont implémentées dans le langage de programmation donné.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Récupère les classes avec l’attribut spécifié dans un module donné.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Récupère le point d’entrée de l’application.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Récupère l’adresse d’une fonction qui représente le décalage de la ligne donnée.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Récupère la structure des variables locales pour un ensemble de méthodes.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Retourne le nom associé au jeton spécifié son objet de métadonnées spécifié.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Récupère les symboles de débogage avec l’attribut parent donné pour le module spécifié.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Récupère le lecteur de symboles pour être utilisé par du code non managé.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Extrait vers un type de symbole donné son adresse de débogage.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Détermine si la fonction à l’adresse de débogage spécifié est supprimée.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Détermine si la fonction à l’adresse de débogage spécifiés est considérée comme obsolète.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Détermine si le code à l’adresse de débogueur spécifié est masqué.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Charge les symboles de débogage spécifiés dans la mémoire.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Étant donnés le flux de données de symboles de débogage de charge.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Remplace les symboles de débogage actuelle avec ceux présents dans le flux de données spécifié.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Décharge les symboles de débogage pour le module spécifié de la mémoire.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Met à jour les symboles de débogage dans la mémoire avec celles du flux de données spécifié.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll