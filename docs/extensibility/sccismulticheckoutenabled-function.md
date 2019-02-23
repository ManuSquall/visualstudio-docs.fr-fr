---
title: Fonction SccIsMultiCheckoutEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0b4d13367977081b757fa9b0ef2823154dc348a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679188"
---
# <a name="sccismulticheckoutenabled-function"></a>Fonction SccIsMultiCheckoutEnabled
Cette fonction vérifie si le plug-in de contrôle de code source autorise les extractions multiples sur un fichier.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Paramètres
 pContext

[in] La structure de contexte de plug-in de contrôle de source.

 pbMultiCheckout

[out] Spécifie si les extractions multiples sont activées pour ce projet (différente de zéro signifie que les extractions multiples sont pris en charge).

## <a name="return-value"></a>Valeur de retour
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :

|Value|Description|
|-----------|-----------------|
|SCC_OK|La vérification a réussi.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Erreur non spécifique.|

## <a name="remarks"></a>Notes
 L’IDE effectue deux vérifications pour déterminer si les fichiers peuvent être extraits simultanément par plusieurs utilisateurs. Tout d’abord, le système de contrôle de source doit prendre en charge les extractions multiples. Le plug-in de contrôle de code source peut spécifier cette fonctionnalité lors de l’initialisation en spécifiant le `SCC_CAP_MULTICHECKOUT`. Par la suite, une deuxième vérification, l’IDE appelle cette fonction pour déterminer si le projet actuel prend en charge les extractions multiples. Si les extractions multiples sont pris en charge pour le projet sélectionné, la plug-in retourne une réussite de code et définit `pbMultiCheckout` à différente de zéro (`TRUE`) ou `FALSE`.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)