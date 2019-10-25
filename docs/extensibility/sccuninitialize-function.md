---
title: SccUninitialize fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 321f50173e3c1517cc6a431ff74933e1a02ef1d0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720132"
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

## <a name="return-value"></a>Valeur de retour
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|valeur|Description|
|-----------|-----------------|
|SCC_OK|Le nettoyage s’est terminé correctement.|

## <a name="remarks"></a>Notes
 Le plug-in de contrôle de code source est responsable de la préparation de l’arrêt et de la libération de mémoire allouée par le plug-in pour la structure de contexte. La fonction est appelée une fois pour chaque instance donnée d’un plug-in. Un appel à [SccInitialize](../extensibility/sccinitialize-function.md) précède cet appel. Aucun projet ne peut encore être ouvert au moment de l’appel à `SccUninitialize`.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)