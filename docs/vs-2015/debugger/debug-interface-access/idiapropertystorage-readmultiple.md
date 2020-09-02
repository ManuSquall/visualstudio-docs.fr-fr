---
title: IDiaPropertyStorage::ReadMultiple | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 40cd84e00f2e6abea285368a6206c7400abf8877
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538081"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lit les propriétés spécifiées à partir du jeu de propriétés actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cpspec`  
 dans Nombre de propriétés spécifiées dans le `rgpspec` tableau. Si la valeur est zéro, la méthode ne retourne aucune propriété, mais retourne `S_OK` comme code de réussite.  
  
 `rgpspec`  
 dans Tableau de propriétés à lire. Les propriétés peuvent être spécifiées à l’aide d’un ID de propriété ou d’un nom de chaîne facultatif. Il n’est pas nécessaire de spécifier des propriétés dans un ordre particulier dans le tableau. Le tableau peut contenir des propriétés dupliquées, ce qui génère des valeurs de propriété en double au retour pour les propriétés simples. Les propriétés non simples doivent retourner l’accès refusé pour une tentative de les ouvrir une deuxième fois. Le tableau peut contenir un mélange d’ID de propriété et d’ID de chaîne. Ce tableau doit avoir au moins un `cpspec` nombre de valeurs de propriété.  
  
 `rgvar`  
 [in, out] Tableau de `PROPVARIANT` structures (dans l’espace de noms Microsoft. VisualStudio. OLE. Interop) à remplir avec les valeurs de chaque propriété. La taille du tableau doit être au moins égale à `cpspec` . L’appelant n’a pas besoin d’initialiser les valeurs dans le tableau.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si une ou plusieurs des propriétés sont introuvables. Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Si une propriété est introuvable, l’entrée correspondante dans le `rgvar` tableau contient un `VARIANT` avec le type de `VT_EMPTY` .  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
