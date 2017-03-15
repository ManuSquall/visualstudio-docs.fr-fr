---
title: "SymTagEnum | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SymTagEnum (énumération)"
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# SymTagEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Spécifie le type de symbole.  
  
## Syntaxe  
  
```cpp#  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## Éléments  
 `SymTagNull`  
 Indique ne qu'aucun type de symbole.  
  
 `SymTagExe`  
 Indique que le symbole est un fichier .exe.  Il n'est qu'un `SymTagExe` symbole par le magasin de symboles.  Il sert à la portée globale et ne possède pas de parent lexical.  
  
 `SymTagCompiland`  
 Indique le symbole de module \(compiland\) pour chaque composant de module \(compiland\) du magasin de symboles.  Pour les applications natives, `SymTagCompiland` symboles correspondent aux fichiers objet liés dans l'image.  Pour certains types d'images du langage MSIL \(Microsoft Intermediate Language\), il existe un module \(compiland\) par classe.  
  
 `SymTagCompilandDetails`  
 Indique que le symbole contient des attributs étendus de la module \(compiland\).  Récupération de ces propriétés peut\-être nécessiter le chargement de symboles de module \(compiland\).  
  
 `SymTagCompilandEnv`  
 Indique que le symbole est une chaîne d'environnement définie pour le module \(compiland\).  
  
 `SymTagFunction`  
 Indique que le symbole est une fonction.  
  
 `SymTagBlock`  
 Indique que le symbole est un bloc imbriqué.  
  
 `SymTagData`  
 Indique que le symbole de données.  
  
 `SymTagAnnotation`  
 Indique que le symbole est pour une annotation du code.  Enfants de ce symbole sont des chaînes de données constant \(`SymTagData`, `LocIsConstant`, `DataIsConstant`\).  La plupart des clients ignorent ce symbole.  
  
 `SymTagLabel`  
 Indique que le symbole est une étiquette.  
  
 `SymTagPublicSymbol`  
 Indique que le symbole est un symbole public.  Pour les applications natives, ce symbole est le symbole externe COFF rencontré lors de la liaison de l'image.  
  
 `SymTagUDT`  
 Indique que le symbole est un type défini par l'utilisateur \(classe, structure ou union\).  
  
 `SymTagEnum`  
 Indique que le symbole est une énumération.  
  
 `SymTagFunctionType`  
 Indique que le symbole est un type de signature de fonction.  
  
 `SymTagPointerType`  
 Indique que le symbole est un type pointeur.  
  
 `SymTagArrayType`  
 Indique que le symbole est un type de tableau.  
  
 `SymTagBaseType`  
 Indique que le symbole est un type de base.  
  
 `SymTagTypedef`  
 Indique que le symbole est un `typedef`, c'est\-à\-dire, un alias pour un autre type.  
  
 `SymTagBaseClass`  
 Indique que le symbole est une classe de base d'un type défini par l'utilisateur.  
  
 `SymTagFriend`  
 Indique que le symbole est un ami d'un type défini par l'utilisateur.  
  
 `SymTagFunctionArgType`  
 Indique que le symbole est un argument de fonction.  
  
 `SymTagFuncDebugStart`  
 Indique que le symbole est l'emplacement de fin du code de prologue de la fonction.  
  
 `SymTagFuncDebugEnd`  
 Indique que le symbole est l'emplacement de début du code d'épilogue de la fonction.  
  
 `SymTagUsingNamespace`  
 Indique que le symbole est un espace de noms, active dans la portée actuelle.  
  
 `SymTagVTableShape`  
 Indique que le symbole est une description de la table virtuelle.  
  
 `SymTagVTable`  
 Indique que le symbole est un pointeur de la table virtuelle.  
  
 `SymTagCustom`  
 Indique que le symbole est un symbole personnalisé et n'est pas interprété par diamètre  
  
 `SymTagThunk`  
 Indique que le symbole est un thunk utilisé pour partager des données entre 16 et 32 bits.  
  
 `SymTagCustomType`  
 Indique que le symbole est un symbole de compilation personnalisés.  
  
 `SymTagManagedType`  
 Indique que le symbole est dans les métadonnées.  
  
 `SymTagDimension`  
 Indique que le symbole est un tableau multidimensionnel FORTRAN.  
  
 `SymTagCallSite`  
 Indique que le symbole représente le site d'appel.  
  
 `SymTagInlineSite`  
 Indique que le symbole représente le site en ligne.  
  
 `SymTagBaseInterface`  
 Indique que le symbole est une interface de base.  
  
 `SymTagVectorType`  
 Indique que le symbole est un type de vecteur.  
  
 `SymTagMatrixType`  
 Indique que le symbole est un type de matrice.  
  
 `SymTagHLSLType`  
 Indique que le symbole est un type High Level Shader Language.  
  
## Notes  
 Tous les symboles au sein d'un fichier de débogage ont une balise d'identification qui spécifie le type du symbole.  
  
 Les valeurs de cette énumération sont retournées par un appel à la [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md) méthode.  
  
 Les valeurs de cette énumération sont passés aux méthodes suivantes pour limiter la portée de la recherche à un type de symbole spécifique :  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## Configuration requise  
 En\-tête : cvconst.h  
  
## Voir aussi  
 [Énumérations et structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)   
 [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)   
 [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)