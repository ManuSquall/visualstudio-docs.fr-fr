---
description: Le tableau suivant présente les types de symboles dans la hiérarchie lexicale.
title: Hiérarchie lexicale des types de symboles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 605b16d2a53178b52095e9919c10bba53f3f21a1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155389"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Hiérarchie lexicale des types de symboles
Le tableau suivant présente les types de symboles dans la hiérarchie lexicale.

## <a name="symbol-types"></a>Types de symboles

|Type de symbole|Description|
|-----------------|-----------------|
|[Annotation](../../debugger/debug-interface-access/annotation.md)|Spécifie un emplacement annoté dans le code de programme.|
|[Bloquer](../../debugger/debug-interface-access/block.md)|Spécifie des portées imbriquées dans les fonctions.|
|`Compiland`|Spécifie un `compiland` lié au fichier. exe.|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Spécifie les données du compiland qui peuvent nécessiter le chargement de détails supplémentaires sur le module de la mémoire et, par conséquent, entraîner une surcharge d’exécution.|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Spécifie toutes les variables d’environnement supplémentaires significatives pour la compilation du compiland.|
|[Personnalisé (Kit de développement logiciel de Debug Interface Access)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Spécifie un symbole défini par l’utilisateur.|
|[Données (SDK Debug Interface Access)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Spécifie des variables telles que les paramètres, les variables locales, les variables globales et les membres de classe.|
|[Exe](../../debugger/debug-interface-access/exe.md)|Spécifie l’étendue globale des données ; correspond à un fichier. exe ou. dll entier.|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Spécifie une fonction qui a un point défini auquel le débogage doit se terminer.|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Spécifie une fonction qui a un point défini à partir duquel le débogage doit commencer.|
|[Fonction (SDK Debug Interface Access)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Spécifie une fonction.|
|[Étiquette (Kit de développement logiciel de Debug Interface Access)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Spécifie un emplacement dans le code de programme.|
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Spécifie un symbole externe qui s’affiche lors de la génération du programme exécutable.|
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Spécifie un `thunk` .|
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Spécifie un `namespace` identificateur.|

> [!NOTE]
> Des propriétés de symboles supplémentaires peuvent être disponibles selon le type de symbole. Ces propriétés sont répertoriées dans les rubriques individuelles relatives aux symboles.

## <a name="see-also"></a>Voir aussi
- [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
- [Symboles et étiquettes de symbole](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [SymTagEnum, énumération](../../debugger/debug-interface-access/symtagenum.md)
