---
title: span::span, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9fe89b289601775fad8c102e696e799edce1c50c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35669011"
---
# <a name="spanspan-constructor"></a>span::span, constructeur
Initialise une nouvelle instance de la classe `span`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
span(  
   const marker_series& _Series,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `_Series`  
 Contexte valide de la série de marqueurs.  
  
 `_Format`  
 Chaîne de mise en forme composite contenant du texte associé à zéro, un ou plusieurs éléments de mise en forme qui correspondent aux objets de la liste d’arguments.  
  
 `_Importance`  
 Niveau d’importance.  
  
 `_Category`  
 Catégorie.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** *cvmarkersobj.h*  
  
 **Espace de noms** : Concurrency::diagnostic
 
 ## <a name="see-also"></a>Voir aussi
 [span, classe](../profiling/span-class.md)