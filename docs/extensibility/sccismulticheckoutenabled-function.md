---
title: SccIsMultiCheckoutEnabled fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd8fb5439ac68200ba1a3bbf3af665595528173e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721083"
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

dans Structure de contexte du plug-in de contrôle de code source.

 pbMultiCheckout

à Spécifie si plusieurs extractions sont activées pour ce projet (une valeur différente de zéro signifie que plusieurs extractions sont prises en charge).

## <a name="return-value"></a>Valeur de retour
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|valeur|Description|
|-----------|-----------------|
|SCC_OK|La vérification a réussi.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Échec non spécifique.|

## <a name="remarks"></a>Notes
 L’IDE effectue deux vérifications pour déterminer si les fichiers peuvent être extraits simultanément par plusieurs utilisateurs. Tout d’abord, le système de contrôle de code source doit prendre en charge les extractions multiples. Le plug-in de contrôle de code source peut spécifier cette fonctionnalité pendant l’initialisation en spécifiant le `SCC_CAP_MULTICHECKOUT`. Par la suite, dans le cadre d’une deuxième vérification, l’IDE appelle cette fonction pour déterminer si le projet actuel prend en charge les extractions multiples. Si plusieurs extractions sont prises en charge pour le projet sélectionné, le plug-in retourne un code de réussite et définit `pbMultiCheckout` sur une valeur différente de zéro (`TRUE`) ou `FALSE`.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)