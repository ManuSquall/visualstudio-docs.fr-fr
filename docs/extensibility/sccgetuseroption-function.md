---
title: Fonction SccGetUserOption (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc7b68df3331c1240ad833048940e656da034ccf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700690"
---
# <a name="sccgetuseroption-function"></a>Fonction SccGetUserOption
Cette fonction récupère une variété d’options spécifiques à l’utilisateur.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Paramètres
 pContext

[dans] Le pointeur de contexte de plug-in de contrôle de source.

 nOption

[dans] Option de récupération (voir Remarques pour les options possibles).

 lpVal (en)

[out] Valeur associée à l’option.

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’option a été récupérée avec succès.|
|SCC_E_OPNOTSUPPORTED|L’option n’est pas prise en charge.|
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée s'est produite.|

## <a name="remarks"></a>Notes
 Les options suivantes sont prises en charge par cette commande :

|Option utilisateur|Description|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Détermine si l’utilisateur veut vérifier la version locale des fichiers. `lpVal`est `SCC_USEROPT_COLV_YES` affecté (l’utilisateur veut vérifier `SCC_USEROPT_COLV_NO`les fichiers locaux) ou .|

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Codes d’erreur](../extensibility/error-codes.md)
