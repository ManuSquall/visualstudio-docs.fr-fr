---
title: Fonction SccSetOption (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1adcbb47e9fce7037fe8942326e8836ade51e3eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700307"
---
# <a name="sccsetoption-function"></a>Fonction SccSetOption
Cette fonction définit les options qui contrôlent le comportement du plug-in de contrôle source.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccSetOption(
   LPVOID pvContext,
   LONG   nOption,
   LONG   dwVal
);
```

#### <a name="parameters"></a>Paramètres
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 nOption

[dans] L’option qui est en cours de jeu.

 dwVal (en)

[dans] Paramètres pour l’option.

## <a name="return-value"></a>Valeur de retour
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|L’option a été réglée avec succès.|
|SCC_I_SHARESUBPROJOK|Retourné `nOption` si `SCC_OPT_SHARESUBPROJ` était et le plug-in de contrôle source permet à l’IDE de définir le dossier de destination.|
|SCC_E_OPNOTSUPPORTED|L’option n’a pas été définie et ne devrait pas être invoquée.|

## <a name="remarks"></a>Notes
 L’IDE appelle cette fonction pour contrôler le comportement du plug-in de contrôle source. Le premier `nOption`paramètre, indique la valeur qui est `dwVal`définie, tandis que le second, indique ce qu’il faut faire avec cette valeur. Le plug-in stocke cette `pvContext``,` information associée à un si l’IDE doit appeler cette fonction après avoir appelé le [SccInitialize](../extensibility/sccinitialize-function.md) (mais pas nécessairement après chaque appel à la [SccOpenProject](../extensibility/sccopenproject-function.md)).

 Résumé des options et de leurs valeurs :

|`nOption`|`dwValue`|Description|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Permet/désactive la file d’attente de l’événement de fond.|
|`SCC_OPT_USERDATA`|Valeur arbitraire|Précise une valeur utilisateur à transmettre à la fonction de rappel [OPTNAMECHANGEPFN.](../extensibility/optnamechangepfn.md)|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Indique si l’IDE prend actuellement en charge l’annulation d’une opération.|
|`SCC_OPT_NAMECHANGEPFN`|Pointeur vers la fonction de rappel [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)|Définit un pointeur vers une fonction de rappel de changement de nom.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Indique si l’IDE permet de vérifier manuellement ses fichiers (via l’interface utilisateur de contrôle source) ou si elles ne doivent être vérifiées que par le plug-in de contrôle source.|
|`SCC_OPT_SHARESUBPROJ`|N/A|Si le plug-in de contrôle source permet à l’IDE de `SCC_I_SHARESUBPROJOK`spécifier le dossier de projet local, le plug-in revient .|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Si `nOption` `SCC_OPT_EVENTQUEUE`c’est le cas, l’IDE désactive (ou réactive) le traitement de fond. Par exemple, lors d’une compilation, l’IDE peut ordonner au plug-in de contrôle source d’arrêter le traitement inactif de toute nature. Après la compilation, il réhabilitait le traitement de fond pour maintenir la file d’attente de l’événement plug-in à jour. Correspondant à `SCC_OPT_EVENTQUEUE` la `nOption`valeur de , `dwVal`il ya `SCC_OPT_EQ_ENABLE` `SCC_OPT_EQ_DISABLE`deux valeurs possibles pour , à savoir, et .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Si la `nOption` valeur `SCC_OPT_HASCANCELMODE`est, l’IDE permet aux utilisateurs d’annuler les opérations longues. Le `dwVal` `SCC_OPT_HCM_NO` paramètre à (la valeur par défaut) indique que l’IDE n’a pas de mode d’annulation. Le plug-in de contrôle source doit offrir son propre bouton Annuler s’il veut que l’utilisateur puisse annuler. `SCC_OPT_HCM_YES`indique que l’IDE offre la possibilité d’annuler une opération, de sorte que le plug-in SCC n’a pas besoin d’afficher son propre bouton Annuler. Si `dwVal` l’IDE `SCC_OPT_HCM_YES`s’installe, il `SCC_MSG_STATUS` `DOCANCEL` est prêt `lpTextOutProc` à répondre et les messages envoyés à la fonction de rappel (voir [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). Si l’IDE ne fixe pas cette variable, le plug-in ne doit pas envoyer ces deux messages.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Si nOption est `SCC_OPT_NAMECHANGEPFN`configuré, et le plug-in de contrôle source et l’IDE l’autorisent, le plug-in peut effectivement renommer ou déplacer un fichier lors d’une opération de contrôle source. Le `dwVal` sera réglé sur un pointeur de fonction de type [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md). Lors d’une opération de contrôle source, le plug-in peut appeler cette fonction, en passant en trois paramètres. Il s’agit de l’ancien nom (avec un chemin entièrement qualifié) d’un fichier, le nouveau nom (avec la voie entièrement qualifiée) de ce fichier, et un pointeur à l’information qui a une pertinence pour l’IDE. L’IDE envoie dans ce `SccSetOption` `nOption` dernier `SCC_OPT_USERDATA`pointeur `dwVal` en appelant avec set to , avec pointant vers les données. Le support de cette fonction est facultatif. Un plug-VSSCI qui utilise cette capacité doit initialiser `NULL`son pointeur de fonction et les variables de données utilisateur à , et il ne doit pas appeler une fonction de renom à moins qu’il n’a été donné un. Il devrait également être prêt à détenir la valeur qu’il a `SccSetOption`été donnée ou à la modifier en réponse à un nouvel appel à . Cela ne se produira pas au milieu d’une opération de commandement de contrôle des sources, mais cela peut se produire entre les commandes.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Si nOption est `SCC_OPT_SCCCHECKOUTONLY`configuré, l’IDE indique que les fichiers du projet actuellement ouvert ne doivent jamais être vérifiés manuellement via l’interface utilisateur du système de contrôle source. Au lieu de cela, les fichiers ne doivent être vérifiés que par le biais du plug-in de contrôle source sous contrôle IDE. Si `dwValue` elle `SCC_OPT_SCO_NO`est configuré, cela signifie que les fichiers doivent être traités normalement par le plug-in et peuvent être vérifiés par l’interface utilisateur de contrôle source. Si `dwValue` elle `SCC_OPT_SCO_YES`est configuré, alors seul le plug-in est autorisé à vérifier les fichiers, et l’interface utilisateur du système de contrôle source ne doit pas être invoquée. Il s’agit de situations où l’IDE pourrait avoir des "pseudo-fichiers" qui ont du sens de vérifier uniquement à travers l’IDE.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Si`nOption` elle `SCC_OPT_SHARESUBPROJ`est configuré, l’IDE teste si le plug-in de contrôle source peut utiliser un dossier local spécifié lors de l’ajout de fichiers à partir du contrôle source. La valeur `dwVal` du paramètre n’a pas d’importance en l’espèce. Si le plug-in permet à l’IDE de spécifier le dossier de destination local où les fichiers seront ajoutés `SCC_I_SHARESUBPROJOK` à `SccSetOption` partir du contrôle source lorsque le [SccAddFromScc](../extensibility/sccaddfromscc-function.md) est appelé, alors le plug-in doit revenir lorsque la fonction est appelée. L’IDE utilise `lplpFileNames` ensuite `SccAddFromScc` le paramètre de la fonction pour passer dans le dossier de destination. Le plug-in utilise ce dossier de destination pour placer les fichiers ajoutés à partir du contrôle source. Si le plug-in `SCC_I_SHARESUBPROJOK` ne `SCC_OPT_SHARESUBPROJ` revient pas lorsque l’option est définie, l’IDE suppose que le plug-in est en mesure d’ajouter des fichiers uniquement dans le dossier local actuel.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
