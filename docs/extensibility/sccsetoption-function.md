---
description: Cette fonction définit des options qui contrôlent le comportement du plug-in de contrôle de code source.
title: SccSetOption fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 18e33cbb8dbee9b332456826ed33e46e4d2e76de
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904098"
---
# <a name="sccsetoption-function"></a>Fonction SccSetOption
Cette fonction définit des options qui contrôlent le comportement du plug-in de contrôle de code source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccSetOption(
   LPVOID pvContext,
   LONG   nOption,
   LONG   dwVal
);
```

#### <a name="parameters"></a>Paramètres
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 nOption

dans Option définie.

 dwVal

dans Paramètres de l’option.

## <a name="return-value"></a>Valeur renvoyée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’option a été correctement définie.|
|SCC_I_SHARESUBPROJOK|Retourné si `nOption` a `SCC_OPT_SHARESUBPROJ` la valeur et que le plug-in de contrôle de code source permet à l’IDE de définir le dossier de destination.|
|SCC_E_OPNOTSUPPORTED|L’option n’a pas été définie et ne doit pas être fiable.|

## <a name="remarks"></a>Remarques
 L’IDE appelle cette fonction pour contrôler le comportement du plug-in de contrôle de code source. Le premier paramètre, `nOption` , indique la valeur qui est définie, tandis que la seconde, `dwVal` , indique que faire avec cette valeur. Le plug-in stocke ces informations associées à un `pvContext``,` , de sorte que l’IDE doit appeler cette fonction après l’appel de [SccInitialize](../extensibility/sccinitialize-function.md) (mais pas nécessairement après chaque appel à [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Résumé des options et de leurs valeurs :

|`nOption`|`dwValue`|Description|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Active/désactive la mise en file d’attente des événements en arrière-plan.|
|`SCC_OPT_USERDATA`|Valeur arbitraire|Spécifie une valeur utilisateur à passer à la fonction de rappel [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) .|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indique si l’IDE prend actuellement en charge l’annulation d’une opération.|
|`SCC_OPT_NAMECHANGEPFN`|Pointeur vers la fonction de rappel [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Définit un pointeur vers une fonction de rappel de modification de nom.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indique si l’IDE autorise l’extraction manuelle de ses fichiers (via l’interface utilisateur du contrôle de code source) ou s’ils doivent être extraits uniquement via le plug-in de contrôle de code source.|
|`SCC_OPT_SHARESUBPROJ`|N/A|Si le plug-in de contrôle de code source permet à l’IDE de spécifier le dossier de projet local, le plug-in retourne `SCC_I_SHARESUBPROJOK` .|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Si `nOption` est `SCC_OPT_EVENTQUEUE` , l’IDE désactive (ou réactiver) le traitement en arrière-plan. Par exemple, lors d’une compilation, l’IDE peut demander au plug-in de contrôle de code source d’arrêter le traitement d’inactivité de n’importe quel type. Après la compilation, elle réactiverait le traitement en arrière-plan pour maintenir à jour la file d’attente d’événements du plug-in. Correspondant à la `SCC_OPT_EVENTQUEUE` valeur de `nOption` , il existe deux valeurs possibles pour `dwVal` , à savoir, `SCC_OPT_EQ_ENABLE` et `SCC_OPT_EQ_DISABLE` .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Si la valeur de `nOption` est `SCC_OPT_HASCANCELMODE` , l’IDE permet aux utilisateurs d’annuler des opérations de longue durée. L’affectation de la valeur `dwVal` `SCC_OPT_HCM_NO` (valeur par défaut) indique que l’IDE n’a pas de mode d’annulation. Le plug-in de contrôle de code source doit proposer son propre bouton Annuler s’il veut que l’utilisateur puisse annuler. `SCC_OPT_HCM_YES` indique que l’IDE offre la possibilité d’annuler une opération, le plug-in SCC n’a donc pas besoin d’afficher son propre bouton d’annulation. Si l’IDE affecte `dwVal` à la valeur `SCC_OPT_HCM_YES` , il est prêt à répondre aux `SCC_MSG_STATUS` `DOCANCEL` messages et envoyés à la `lpTextOutProc` fonction de rappel (voir [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Si l’IDE ne définit pas cette variable, le plug-in ne doit pas envoyer ces deux messages.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Si nOption a la valeur `SCC_OPT_NAMECHANGEPFN` , et que le plug-in de contrôle de code source et l’IDE l’autorisent, le plug-in peut en fait renommer ou déplacer un fichier pendant une opération de contrôle de code source. `dwVal`Aura pour valeur un pointeur de fonction de type [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Pendant une opération de contrôle de code source, le plug-in peut appeler cette fonction, en passant trois paramètres. Il s’agit de l’ancien nom (avec le chemin d’accès qualifié complet) d’un fichier, du nouveau nom (avec le chemin d’accès qualifié complet) de ce fichier, et d’un pointeur vers les informations qui sont pertinentes pour l’IDE. L’IDE envoie dans ce dernier pointeur en appelant `SccSetOption` avec `nOption` défini sur `SCC_OPT_USERDATA` , en `dwVal` pointant vers les données. La prise en charge de cette fonction est facultative. Un plug-in VSSCI qui utilise cette capacité doit initialiser son pointeur de fonction et les variables de données utilisateur à `NULL` , et il ne doit pas appeler une fonction Rename, sauf si elle en a reçu une. Vous devez également être prêt à conserver la valeur qu’elle a été donnée ou à la modifier en réponse à un nouvel appel à `SccSetOption` . Cela ne se produit pas au milieu d’une opération de commande de contrôle de code source, mais il peut se produire entre les commandes.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Si nOption a la valeur `SCC_OPT_SCCCHECKOUTONLY` , l’IDE indique que les fichiers du projet actuellement ouvert ne doivent jamais être extraits manuellement par le biais de l’interface utilisateur du système de contrôle de code source. Au lieu de cela, les fichiers doivent être extraits uniquement via le plug-in de contrôle de code source sous contrôle IDE. Si `dwValue` a la valeur `SCC_OPT_SCO_NO` , cela signifie que les fichiers doivent être traités normalement par le plug-in et peuvent être extraits par le biais de l’interface utilisateur du contrôle de code source. Si `dwValue` a la valeur `SCC_OPT_SCO_YES` , seul le plug-in est autorisé à extraire les fichiers et l’interface utilisateur du système de contrôle de code source ne doit pas être appelée. C’est le cas pour les situations où l’IDE peut avoir des « Pseudo-fichiers » qui ont un sens pour l’extraction uniquement via l’IDE.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Si `nOption` a la valeur `SCC_OPT_SHARESUBPROJ` , l’IDE teste si le plug-in de contrôle de code source peut utiliser un dossier local spécifié lors de l’ajout de fichiers à partir du contrôle de code source. La valeur du `dwVal` paramètre n’a pas d’importance dans ce cas. Si le plug-in permet à l’IDE de spécifier le dossier de destination local dans lequel les fichiers sont ajoutés à partir du contrôle de code source lorsque le [SccAddFromScc](../extensibility/sccaddfromscc-function.md) est appelé, le plug-in doit retourner `SCC_I_SHARESUBPROJOK` lorsque la `SccSetOption` fonction est appelée. L’IDE utilise ensuite le `lplpFileNames` paramètre de la `SccAddFromScc` fonction pour passer dans le dossier de destination. Le plug-in utilise ce dossier de destination pour placer les fichiers ajoutés à partir du contrôle de code source. Si le plug-in n’est pas retourné `SCC_I_SHARESUBPROJOK` lorsque l' `SCC_OPT_SHARESUBPROJ` option est définie, l’IDE suppose que le plug-in est en mesure d’ajouter des fichiers uniquement dans le dossier local actuel.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
