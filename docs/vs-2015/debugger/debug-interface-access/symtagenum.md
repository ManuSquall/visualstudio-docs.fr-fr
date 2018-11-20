---
title: SymTagEnum | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09462ee9d9223c79b4ee0dcf4e8a5efa37b4c796
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783298"
---
# <a name="symtagenum"></a>SymTagEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Spécifie le type de symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="elements"></a>Éléments  
 `SymTagNull`  
 Indique que le symbole n’a aucun type.  
  
 `SymTagExe`  
 Indique que le symbole est un fichier .exe. Il existe un seul `SymTagExe` symbole par un magasin de symboles. Il sert à la portée globale et n’a pas de parent lexical.  
  
 `SymTagCompiland`  
 Indique le symbole de compiland pour chaque composant de compiland du magasin de symboles. Pour les applications natives, `SymTagCompiland` symboles correspondent aux fichiers objet liés dans l’image. Pour certains types d’images de langage MSIL (Microsoft Intermediate Language), il existe un compiland par classe.  
  
 `SymTagCompilandDetails`  
 Indique que le symbole contient des attributs étendus du module. Récupération de ces propriétés peut-être nécessiter le chargement des symboles de compiland.  
  
 `SymTagCompilandEnv`  
 Indique que le symbole est une chaîne d’environnement définie pour le compiland.  
  
 `SymTagFunction`  
 Indique que le symbole est une fonction.  
  
 `SymTagBlock`  
 Indique que le symbole est un bloc imbriqué.  
  
 `SymTagData`  
 Indique que le symbole de données.  
  
 `SymTagAnnotation`  
 Indique que le symbole est pour une annotation de code. Les enfants de ce symbole sont des chaînes de données constantes (`SymTagData`, `LocIsConstant`, `DataIsConstant`). La plupart des clients ignorer ce symbole.  
  
 `SymTagLabel`  
 Indique que le symbole est une étiquette.  
  
 `SymTagPublicSymbol`  
 Indique que le symbole est un symbole public. Pour les applications natives, ce symbole est le symbole externe COFF rencontré lors de la liaison de l’image.  
  
 `SymTagUDT`  
 Indique que le symbole est un type défini par l’utilisateur (classe, structure ou union).  
  
 `SymTagEnum`  
 Indique que le symbole est une énumération.  
  
 `SymTagFunctionType`  
 Indique que le symbole est un type de signature de fonction.  
  
 `SymTagPointerType`  
 Indique que le symbole est un type pointeur.  
  
 `SymTagArrayType`  
 Indique que le symbole est un type tableau.  
  
 `SymTagBaseType`  
 Indique que le symbole est un type de base.  
  
 `SymTagTypedef`  
 Indique que le symbole est un `typedef`, autrement dit, un alias pour un autre type.  
  
 `SymTagBaseClass`  
 Indique que le symbole est une classe de base d’un type défini par l’utilisateur.  
  
 `SymTagFriend`  
 Indique que le symbole est une fonction friend d’un type défini par l’utilisateur.  
  
 `SymTagFunctionArgType`  
 Indique que le symbole est un argument de fonction.  
  
 `SymTagFuncDebugStart`  
 Indique que le symbole est l’emplacement de fin du code de prologue de la fonction.  
  
 `SymTagFuncDebugEnd`  
 Indique que le symbole est l’emplacement de début du code d’épilogue de la fonction.  
  
 `SymTagUsingNamespace`  
 Indique que le symbole est un espace de noms, active dans la portée actuelle.  
  
 `SymTagVTableShape`  
 Indique que le symbole est une description de la table virtuelle.  
  
 `SymTagVTable`  
 Indique que le symbole est un pointeur de la table virtuelle.  
  
 `SymTagCustom`  
 Indique que le symbole est un symbole personnalisé et qu’il n’est pas interprété par DIA.  
  
 `SymTagThunk`  
 Indique que le symbole est un thunk utilisé pour partager des données entre 16 et 32 bits de code.  
  
 `SymTagCustomType`  
 Indique que le symbole est un symbole du compilateur personnalisé.  
  
 `SymTagManagedType`  
 Indique que le symbole est dans les métadonnées.  
  
 `SymTagDimension`  
 Indique que le symbole est un tableau multidimensionnel FORTRAN.  
  
 `SymTagCallSite`  
 Indique que le symbole représente le site d’appel.  
  
 `SymTagInlineSite`  
 Indique que le symbole représente le site inline.  
  
 `SymTagBaseInterface`  
 Indique que le symbole est une interface de base.  
  
 `SymTagVectorType`  
 Indique que le symbole est un type de vecteur.  
  
 `SymTagMatrixType`  
 Indique que le symbole est un type de matrice.  
  
 `SymTagHLSLType`  
 Indique que le symbole est un type High Level Shader Language.  
  
## <a name="remarks"></a>Notes  
 Tous les symboles dans un fichier de débogage ont une balise d’identification qui spécifie le type du symbole.  
  
 Les valeurs dans cette énumération sont retournées par un appel à la [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) (méthode).  
  
 Les valeurs dans cette énumération sont passées aux méthodes suivantes pour limiter l’étendue de la recherche à un type de symbole spécifique :  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : cvconst.h  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations et Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Hiérarchie lexicale des Types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)



