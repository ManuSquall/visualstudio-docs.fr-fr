---
description: Cette fonction récupère une variété d’options spécifiques à l’utilisateur.
title: SccGetUserOption fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c137630e4a29fc534e9bfced16cffe862e07a046
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220623"
---
# <a name="sccgetuseroption-function"></a>Fonction SccGetUserOption
Cette fonction récupère une variété d’options spécifiques à l’utilisateur.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Paramètres
 pContext

dans Pointeur de contexte du plug-in de contrôle de code source.

 nOption

dans Option à récupérer (consultez la section Notes pour connaître les options possibles).

 lpVal

à Valeur associée à l’option.

## <a name="return-value"></a>Valeur renvoyée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|SCC_OK|L’option a été récupérée avec succès.|
|SCC_E_OPNOTSUPPORTED|L’option n’est pas prise en charge.|
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée s'est produite.|

## <a name="remarks"></a>Notes
 Cette commande prend en charge les options suivantes :

|User (option)|Description|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Détermine si l’utilisateur souhaite extraire la version locale des fichiers. `lpVal` est assigné `SCC_USEROPT_COLV_YES` (l’utilisateur souhaite extraire les fichiers locaux) ou `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Codes d’erreur](../extensibility/error-codes.md)
