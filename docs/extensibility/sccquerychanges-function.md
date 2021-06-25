---
description: Cette fonction énumère une liste donnée de fichiers, en fournissant des informations sur les modifications de nom pour chaque fichier via une fonction de rappel.
title: SccQueryChanges fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f93ed14671995502356ae4a19664b14bbd32ce7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900471"
---
# <a name="sccquerychanges-function"></a>Fonction SccQueryChanges
Cette fonction énumère une liste donnée de fichiers, en fournissant des informations sur les modifications de nom pour chaque fichier via une fonction de rappel.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Paramètres
 pContext

dans Pointeur de contexte du plug-in de contrôle de code source.

 Nfichiers

dans Nombre de fichiers dans le `lpFileNames` tableau.

 lpFileNames

dans Tableau de noms de fichiers à propos desquels obtenir des informations.

 pfnCallback

dans Fonction de rappel à appeler pour chaque nom de fichier dans la liste (pour plus d’informations, consultez [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) ).

 pvCallerData

dans Valeur qui sera passée sans modification à la fonction de rappel.

## <a name="return-value"></a>Valeur renvoyée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le processus de requête s’est terminé correctement.|
|SCC_E_PROJNOTOPEN|Le projet n’a pas été ouvert dans le contrôle de code source.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention.|
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée ou générale s’est produite.|

## <a name="remarks"></a>Remarques
 Les modifications interrogées concernent l’espace de noms : en particulier, en renommant, en ajoutant et en supprimant un fichier.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Codes d’erreur](../extensibility/error-codes.md)
