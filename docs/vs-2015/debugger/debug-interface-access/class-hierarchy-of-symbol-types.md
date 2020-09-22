---
title: Hiérarchie de classes des types de symboles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], class hierarchies
ms.assetid: 0ccd6990-4654-44cd-a6f3-bdd82fe90f6c
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a7b3edb0262e3e2b4f0cde51b499e25b04aba51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840118"
---
# <a name="class-hierarchy-of-symbol-types"></a>Hiérarchie de classes des types de symboles
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le tableau suivant décrit les types de symboles dans la hiérarchie de classes.  
  
## <a name="symbol-types"></a>Types de symboles  
  
|Type de symbole|Description|  
|-----------------|-----------------|  
|[UDT](../../debugger/debug-interface-access/udt.md)|Symbole utilisé pour représenter chaque classe, structure et Union.|  
|[Énumération (Kit de développement logiciel SDK de Debug Interface Access)](../../debugger/debug-interface-access/enum-debug-interface-access-sdk.md)|Symbole pour les types énumérés.|  
|[PointerType](../../debugger/debug-interface-access/pointertype.md)|Symbole des types pointeur.|  
|[ArrayType](../../debugger/debug-interface-access/arraytype.md)|Symbole pour les types tableau.|  
|[BaseType](../../debugger/debug-interface-access/basetype.md)|Symbole pour les types de base|  
|[Typedef (Kit de développement logiciel de Debug Interface Access)](../../debugger/debug-interface-access/typedef-debug-interface-access-sdk.md)|Symbole qui introduit des noms pour d’autres types.|  
|[BaseClass](../../debugger/debug-interface-access/baseclass.md)|Symbole utilisé pour chaque classe de base d’un type défini par l’utilisateur (UDT).|  
|[Friend (SDK Debug Interface Access)](../../debugger/debug-interface-access/friend-debug-interface-access-sdk.md)|Symbole pour les classes Friend et les fonctions Friend.|  
|[FunctionType](../../debugger/debug-interface-access/functiontype.md)|Symbole pour chaque signature de fonction unique.|  
|[FunctionArgType](../../debugger/debug-interface-access/functionargtype.md)|Symbole pour chaque paramètre d’une fonction.|  
|[VTableShape](../../debugger/debug-interface-access/vtableshape.md)|Symbole de la taille de la table virtuelle.|  
|[VTable](../../debugger/debug-interface-access/vtable.md)|Symbole d’une table virtuelle.|  
|[CustomType](../../debugger/debug-interface-access/customtype.md)|Symbole pour le type défini par le fournisseur.|  
|[ManagedType](../../debugger/debug-interface-access/managedtype.md)|Symbole pour un type défini dans les métadonnées.|  
|[Dimension](../../debugger/debug-interface-access/dimension.md)|Symbole pour les dimensions de tableau.|  
  
> [!NOTE]
> Chaque symbole peut avoir des propriétés qui contiennent des informations sur le symbole, ainsi que des références à d’autres symboles. Ces propriétés sont répertoriées dans les rubriques individuelles relatives aux symboles.  
  
## <a name="see-also"></a>Voir aussi  
 [Énumération CV_access_e](../../debugger/debug-interface-access/cv-access-e.md)   
 [Hiérarchie lexicale des types de symboles](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Symboles et étiquettes de symbole](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
