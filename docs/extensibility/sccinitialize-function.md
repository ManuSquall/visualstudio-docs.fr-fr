---
description: Cette fonction initialise le plug-in de contrôle de code source et fournit des fonctionnalités et des limites à l’environnement de développement intégré (IDE).
title: SccInitialize fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 633e8909febd758df455a9375f735a93e3407c77
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902525"
---
# <a name="sccinitialize-function"></a>Fonction SccInitialize
Cette fonction initialise le plug-in de contrôle de code source et fournit des fonctionnalités et des limites à l’environnement de développement intégré (IDE).

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>Paramètres
 `ppvContext`

dans Le plug-in de contrôle de code source peut placer un pointeur vers sa structure de contexte ici.

 `hWnd`

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 `lpCallerName`

dans Nom du programme appelant le plug-in de contrôle de code source.

 `lpSccName`

[in, out] Mémoire tampon dans laquelle le plug-in de contrôle de code source place son propre nom (à ne pas dépasser `SCC_NAME_LEN` ).

 `lpSccCaps`

à Retourne les indicateurs de capacité du plug-in de contrôle de code source.

 `lpAuxPathLabel`

[in, out] Mémoire tampon dans laquelle le plug-in de contrôle de code source place une chaîne qui décrit le `lpAuxProjPath` paramètre retourné par [SccOpenProject](../extensibility/sccopenproject-function.md) et [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (à ne pas dépasser `SCC_AUXLABEL_LEN` ).

 `pnCheckoutCommentLen`

à Retourne la longueur maximale autorisée pour un commentaire d’extraction.

 `pnCommentLen`

à Retourne la longueur maximale autorisée pour les autres commentaires.

## <a name="return-value"></a>Valeur renvoyée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Initialisation du contrôle de code source réussie.|
|SCC_E_INITIALIZEFAILED|Le système n’a pas pu être initialisé.|
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à effectuer l’opération spécifiée.|
|SCC_E_NONSPECFICERROR|Échec non spécifique ; le système de contrôle de code source n’a pas été initialisé.|

## <a name="remarks"></a>Remarques
 L’IDE appelle cette fonction lorsqu’il charge pour la première fois le plug-in de contrôle de code source. Il permet à l’IDE de transmettre certaines informations, telles que le nom de l’appelant, au plug-in. L’IDE récupère également certaines informations, telles que la longueur maximale autorisée pour les commentaires et les fonctionnalités du plug-in.

 `ppvContext`Pointe vers un `NULL` pointeur. Le plug-in de contrôle de code source peut allouer une structure pour sa propre utilisation et stocker un pointeur vers cette structure dans `ppvContext` . L’IDE transmet ce pointeur à toute autre fonction API VSSCI, ce qui permet au plug-in d’accéder à des informations de contexte sans avoir recours au stockage global et à prendre en charge plusieurs instances du plug-in. Cette structure doit être désallouée lors de l’appel de [SccUninitialize](../extensibility/sccuninitialize-function.md) .

 Les `lpCallerName` `lpSccName` paramètres et permettent à l’IDE et au plug-in de contrôle de code source d’échanger des noms. Ces noms peuvent être utilisés simplement pour faire la distinction entre plusieurs instances, ou ils peuvent s’afficher dans des menus ou des boîtes de dialogue.

 Le `lpAuxPathLabel` paramètre est une chaîne utilisée comme commentaire pour identifier le chemin d’accès du projet auxiliaire qui est stocké dans le fichier solution et passé au plug-in de contrôle de code source dans un appel à [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] utilise la chaîne "SourceSafe Project :"; d’autres plug-ins de contrôle de code source doivent s’abstenir d’utiliser cette chaîne particulière.

 Le `lpSccCaps` paramètre indique au plug-in de contrôle de code source un emplacement de stockage des indicateurs indiquant les fonctionnalités du plug-in. (Pour obtenir la liste complète des indicateurs de fonctionnalités, consultez [indicateurs de capacité](../extensibility/capability-flags.md)). Par exemple, si le plug-in prévoit d’écrire des résultats dans une fonction de rappel fournie par l’appelant, le plug-in définit le bit de fonctionnalité SCC_CAP_TEXTOUT. Cela signale à l’IDE de créer une fenêtre pour les résultats de contrôle de version.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Indicateurs de capacité](../extensibility/capability-flags.md)
