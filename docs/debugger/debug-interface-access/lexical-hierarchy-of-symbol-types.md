---
title: Hiérarchie lexicale des Types de symboles | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 58c4ef49cb7eabae7608ce417e4f3d5ef99a8284
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473421"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Hiérarchie lexicale des types de symboles
Le tableau suivant montre les types de symboles dans la hiérarchie lexicale.  
  
## <a name="symbol-types"></a>Types de symboles  
  
|Type de symbole|Description|  
|-----------------|-----------------|  
|[Annotation](../../debugger/debug-interface-access/annotation.md)|Spécifie un emplacement annoté dans le code de programme.|  
|[Bloc](../../debugger/debug-interface-access/block.md)|Spécifie les portées imbriquées dans les fonctions.|  
|`Compiland`|Spécifie un `compiland` lié au fichier .exe.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Spécifie les données de compiland nécessitent le chargement des détails de compiland supplémentaires et donc entraîner une baisse exécution surcharge pour récupérer.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Spécifie les variables d’environnement supplémentaires importantes à la compilation de la compiland.|  
|[Personnalisé (Kit de développement logiciel de Debug Interface Access)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Spécifie un symbole défini par l’utilisateur.|  
|[Données (SDK Debug Interface Access)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Spécifie des variables comme paramètres, les variables locales, les variables globales et les membres de classe.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Spécifie la portée globale des données ; correspond à un fichier .exe ou .dll entier.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Spécifie une fonction qui a un point défini sur le débogage est à la fin.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Spécifie une fonction qui a un point défini au débogage doit commencer.|  
|[Fonction (SDK Debug Interface Access)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Spécifie une fonction.|  
|[Étiquette (Kit de développement logiciel de Debug Interface Access)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Spécifie l’emplacement dans le code de programme.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Spécifie un symbole externe qui s’affiche lors de la génération du programme exécutable.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Spécifie un `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Spécifie un `namespace`identificateur.|  
  
> [!NOTE]
>  Propriétés des symboles supplémentaires peuvent être disponibles selon le type de symbole. Ces propriétés sont répertoriées dans les rubriques de symbole individuels.  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchie de classes des Types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Balises Symbols et Symbol](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [SymTagEnum (énumération)](../../debugger/debug-interface-access/symtagenum.md)