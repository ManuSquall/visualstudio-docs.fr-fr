---
title: Fonction SccQueryChanges | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d21dfe4418d033776431f4864f46412a798be204
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62800328"
---
# <a name="sccquerychanges-function"></a>Fonction SccQueryChanges
Cette fonction énumère une liste de fichiers, en fournissant des informations sur les changements de nom pour chaque fichier via une fonction de rappel donnée.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Paramètres
 pContext

[in] Le pointeur de contexte de plug-in de contrôle de code source.

 nFiles

[in] Nombre de fichiers dans `lpFileNames` tableau.

 lpFileNames

[in] Tableau de noms de fichiers pour obtenir des informations.

 pfnCallback

[in] Fonction de rappel à appeler pour chaque nom de fichier dans la liste (voir [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) pour plus d’informations).

 pvCallerData

[in] Valeur qui est transmis sans modification à la fonction de rappel.

## <a name="return-value"></a>Valeur de retour
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|SCC_OK|Le processus de requête s’est terminé correctement.|
|SCC_E_PROJNOTOPEN|Le projet n’a pas été ouvert dans le contrôle de code source.|
|SCC_E_ACCESSFAILURE|Impossible d’accéder au système de contrôle source, probablement en raison de problèmes réseau ou de contention.|
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée ou générale s’est produite.|

## <a name="remarks"></a>Notes
 Les modifications en cours d’interrogation sont à l’espace de noms : en particulier, changement de nom, l’ajout et suppression d’un fichier.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Codes d’erreur](../extensibility/error-codes.md)