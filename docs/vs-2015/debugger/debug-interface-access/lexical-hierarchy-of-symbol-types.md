---
title: Hiérarchie lexicale des Types de symboles | Microsoft Docs
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
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfb8fd751d6230dd839d073a61e80cabf5d48892
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305485"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Hiérarchie lexicale des types de symboles
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le tableau suivant présente les types de symboles dans la hiérarchie lexicale.  
  
## <a name="symbol-types"></a>Types de symboles  
  
|Type de symbole|Description|  
|-----------------|-----------------|  
|[Annotation](../../debugger/debug-interface-access/annotation.md)|Spécifie un emplacement annoté dans le code de programme.|  
|[Bloc](../../debugger/debug-interface-access/block.md)|Spécifie les portées imbriquées dans les fonctions.|  
|`Compiland`|Spécifie un `compiland` lié au fichier .exe.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Spécifie les données de compiland qui peuvent nécessiter le chargement des détails de compiland supplémentaires et entraînent donc exécuter-une surcharge de temps pour récupérer.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Spécifie les variables d’environnement supplémentaires significatifs à la compilation de la compiland.|  
|[Personnalisé (Kit de développement logiciel de Debug Interface Access)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Spécifie un symbole défini par l’utilisateur.|  
|[Données (SDK Debug Interface Access)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Spécifie des variables en tant que paramètres, les variables locales, les variables globales et les membres de classe.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Spécifie la portée globale des données. correspond à un fichier .exe ou .dll entier.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Spécifie une fonction qui a un point défini sur lequel le débogage consiste à se terminer.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Spécifie une fonction qui a un point défini sur lequel le débogage consiste à commencer.|  
|[Fonction (SDK Debug Interface Access)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Spécifie une fonction.|  
|[Étiquette (Kit de développement logiciel de Debug Interface Access)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Spécifie un emplacement dans le code de programme.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Spécifie un symbole externe qui s’affiche lors de la génération du programme exécutable.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Spécifie un `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Spécifie un `namespace`identificateur.|  
  
> [!NOTE]
>  Propriétés des symboles supplémentaires peuvent être disponibles selon le type de symbole. Ces propriétés sont répertoriées dans les rubriques de symbole individuels.  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchie de classes des Types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Balises Symbols et Symbol](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)



