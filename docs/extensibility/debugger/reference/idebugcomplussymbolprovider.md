---
title: "IDebugComPlusSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugComPlusSymbolProvider"
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Représente un fournisseur de symbole COM\+ avec les méthodes qui sont spécifiques au code managé.  
  
## Syntaxe  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## Remarques à l'intention des implémenteurs  
 Bien qu'il n'y a pas de séparation entre les interfaces qui sont utiles à un évaluateur d' \(EE\)expression et ceux qui sont destinées à être utilisées par un \(DE\) moteur de débogage, les méthodes suivantes se probablement interest DE developers uniquement : AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols, et UpdateSymbols.  
  
## Méthodes  
 En plus de les méthodes sur l'interface d' [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) , cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[AreSymbolsLoaded](../Topic/IDebugComPlusSymbolProvider::AreSymbolsLoaded.md)|Détermine si les symboles de débogage sont chargés pour le module spécifié donné l'identificateur du domaine d'application.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|crée un type du type primitif spécifié.|  
|[GetAddressesInModuleFromPosition](../Topic/IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition.md)|Mappe une position de document dans le module spécifié à un tableau d'adresses de débogage.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Extrait les informations de type à propos de le tableau spécifié données son adresse de débogage.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Extrait le nom de l'assembly avec son module et domaine d'application.|  
|[GetAttributedClassesForLanguage](../Topic/IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage.md)|Récupère les classes avec l'attribut spécifié qui sont implémentées dans le langage de programmation donné.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Récupère les classes avec l'attribut spécifié dans un module donné.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Récupère le point d'entrée de l'application.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Récupère l'adresse d'une fonction qui représente le décalage donné de ligne.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Extrait la disposition des variables locales pour un ensemble de méthodes.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Retourne le nom associé au jeton spécifié avec son objet de métadonnées.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Récupère les symboles de débogage avec l'attribut parent donné pour le module spécifié.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Récupère le lecteur de symboles à utiliser par du code non managé.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|extrait au symbole un type donné son adresse de débogage.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|détermine si la fonction à l'adresse spécifiée de débogage est supprimée.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Détermine si la fonction à l'adresse spécifiée de débogage est considérée comme périmées.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Détermine si le code à l'adresse spécifiée de débogueur est masqué.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Charge les symboles spécifiés de débogage en mémoire.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|symboles de débogage de charges donnés le flux de données.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Remplace les symboles en cours de débogage avec ceux du flux de données spécifié.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|décharge les symboles de débogage pour le module spécifié de la mémoire.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Met à jour les symboles de débogage dans la mémoire avec celles le flux de données spécifié.|  
  
## Configuration requise  
 en\-tête : Sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll