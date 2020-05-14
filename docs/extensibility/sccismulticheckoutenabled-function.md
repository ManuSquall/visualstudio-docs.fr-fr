---
title: Fonction SccIsMultiCheckoutEnabled (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e91eb566a820f4fe11ceb629643e1815dcb87a8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700583"
---
# <a name="sccismulticheckoutenabled-function"></a>Fonction SccIsMultiCheckoutEnabled
Cette fonction vérifie si le plug-in de contrôle source permet plusieurs caisses sur un fichier.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Paramètres
 pContext

[dans] La structure de contexte de plug-in de contrôle de source.

 pbMultiCheckout

[out] Précise si plusieurs caisses sont activées pour ce projet (ce qui signifie que plusieurs caisses sont prises en charge).

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Le chèque a été réussi.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Défaillance non spécifique.|

## <a name="remarks"></a>Notes
 L’IDE effectue deux vérifications pour déterminer si les fichiers peuvent être vérifiés simultanément par plus d’un utilisateur. Tout d’abord, le système de contrôle à la source doit prendre en charge plusieurs caisses. Le plug-in de contrôle source peut spécifier cette capacité lors de l’initialisation en spécifiant le `SCC_CAP_MULTICHECKOUT`. Par la suite, à titre de deuxième vérification, l’IDE appelle cette fonction pour déterminer si le projet actuel prend en charge plusieurs caisses. Si plusieurs caisses sont prises en charge pour le projet sélectionné, le plug-in renvoie un code de réussite et se définit `pbMultiCheckout` à nonzero (`TRUE`) ou `FALSE`.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
