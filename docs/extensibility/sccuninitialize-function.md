---
description: Cette fonction nettoie toutes les allocations ou les connexions ouvertes créées par un appel précédent à SccInitialize en préparation de l’arrêt du plug-in de contrôle de code source.
title: SccUninitialize fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d46aedd3e962d0684689ff29a34061b777fe08e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904072"
---
# <a name="sccuninitialize-function"></a>Fonction SccUninitialize
Cette fonction nettoie toutes les allocations ou les connexions ouvertes créées par un appel précédent à [SccInitialize](../extensibility/sccinitialize-function.md) en préparation de l’arrêt du plug-in de contrôle de code source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Paramètres
 pvContext

dans Pointeur vers la structure de contexte du plug-in de contrôle de code source créée dans [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Valeur renvoyée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le nettoyage s’est terminé correctement.|

## <a name="remarks"></a>Remarques
 Le plug-in de contrôle de code source est responsable de la préparation de l’arrêt et de la libération de mémoire allouée par le plug-in pour la structure de contexte. La fonction est appelée une fois pour chaque instance donnée d’un plug-in. Un appel à [SccInitialize](../extensibility/sccinitialize-function.md) précède cet appel. Aucun projet ne peut encore être ouvert au moment de l’appel à `SccUninitialize` .

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
