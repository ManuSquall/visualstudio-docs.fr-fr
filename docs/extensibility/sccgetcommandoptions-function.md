---
title: Fonction SccGetCommandOptions (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eeefa26422476ca40e782df3ff35eee9d429a149
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700831"
---
# <a name="sccgetcommandoptions-function"></a>Fonction SccGetCommandOptions
Cette fonction invite l’utilisateur pour des options avancées pour une commande donnée.

## <a name="syntax"></a>Syntaxe

```cpp
SCCRTN SccGetCommandOptions(
   LPVOID pvContext,
   HWND hWnd,
   enum SCCCOMMAND iCommand,
   LPCMDOPTS* ppvOptions
);
```

### <a name="parameters"></a>Paramètres
 pvContexte

[dans] La structure de contexte de plug-in de contrôle de source.

 hWnd

[dans] Une poignée à la fenêtre IDE que le plug-in de contrôle source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 Icommand

[dans] La commande pour laquelle des options avancées sont demandées (voir [code de commande](../extensibility/command-code-enumerator.md) pour les valeurs possibles).

 ppvOptions

[dans] La structure d’option `NULL`(peut également être ).

## <a name="return-value"></a>Valeur retournée
 La mise en œuvre plug-in de cette fonction de contrôle source devrait renvoyer l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Réussite.|
|SCC_I_ADV_SUPPORT|Le plug-in de contrôle source prend en charge les options avancées pour la commande.|
|SCC_I_OPERATIONCANCELED|L’utilisateur a annulé la boîte de dialogue **Options** du plug-in de contrôle source.|
|SCC_E_OPTNOTSUPPORTED|Le plug-in de contrôle source ne prend pas en charge cette opération.|
|SCC_E_ISCHECKEDOUT|Impossible d’effectuer cette opération sur un fichier qui est actuellement vérifié.|
|SCC_E_ACCESSFAILURE|Il y avait un problème d’accès au système de contrôle à la source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECIFICERROR|Défaillance non spécifique.|

## <a name="remarks"></a>Notes
 L’IDE appelle cette fonction `ppvOptions` = `NULL` pour la première fois pour déterminer si le plug-in de contrôle source prend en charge la fonction d’options avancées pour la commande spécifiée. Si le plug-in prend en charge la fonctionnalité pour cette commande, l’IDE appelle à nouveau cette fonction lorsque l’utilisateur demande `ppvOptions` des options `NULL` avancées (généralement implémentée comme un bouton **Avancé** dans une boîte de dialogue) et fournit un pointeur non-NULL pour ce point à un pointeur. Le plug-in stocke toutes les options avancées spécifiées par l’utilisateur dans une structure privée et renvoie un pointeur à cette structure en `ppvOptions`. Cette structure est ensuite transmise à toutes les autres fonctions d’API de contrôle `SccGetCommandOptions` source qui doivent être au courant, y compris les appels ultérieurs à la fonction.

 Un exemple peut aider à clarifier cette situation.

 Un utilisateur choisit la commande **Get** et l’IDE affiche une boîte de dialogue **Get.** L’IDE `SccGetCommandOptions` appelle `iCommand` la `SCC_COMMAND_GET` fonction `ppvOptions` avec `NULL`défini et réglé à . Ceci est interprété par le plug-in de contrôle source comme la question, "Avez-vous des options avancées pour cette commande?" Si le plug-in revient, `SCC_I_ADV_SUPPORT`l’IDE affiche un bouton **Advanced** dans sa boîte de dialogue **Get.**

 La première fois que l’utilisateur clique sur le `SccGetCommandOptions` bouton **Advanced,** l’IDE appelle à nouveau la fonction, cette fois avec un non-qui`NULL``ppvOptions` pointe vers un `NULL` pointeur. Le plug-in affiche sa propre boîte de dialogue **Get Options,** invite l’utilisateur pour des informations, `ppvOptions`met cette information dans sa propre structure, et retourne un pointeur à cette structure en .

 Si l’utilisateur clique à nouveau **sur Advanced** dans la `SccGetCommandOptions` même boîte `ppvOptions`de dialogue, l’IDE appelle à nouveau la fonction sans changer, de sorte que la structure est transmise au plug-in. Cela permet au plug-in de réinitialiser sa boîte de dialogue aux valeurs que l’utilisateur avait précédemment définies. Le plug-in modifie la structure en place avant de revenir.

 Enfin, lorsque l’utilisateur clique **SUR OK** dans la boîte de dialogue **Get de** l’IDE, l’IDE appelle le [SccGet](../extensibility/sccget-function.md), en passant la structure retournée qui `ppvOptions` contient les options avancées.

> [!NOTE]
> La `SCC_COMMAND_OPTIONS` commande est utilisée lorsque l’IDE affiche une boîte de dialogue **Options** qui permet à l’utilisateur de définir des préférences qui contrôlent le fonctionnement de l’intégration. Si le plug-in de contrôle source veut fournir sa propre boîte de dialogue de préférences, il peut l’afficher à partir d’un bouton **avancé** dans la boîte de dialogue des préférences de l’IDE. Le plug-in est le seul responsable de l’obtention et de la persistance de cette information; l’IDE ne l’utilise pas ou ne le modifie pas.

## <a name="see-also"></a>Voir aussi
- [Fonctions d’API plug-in de contrôle des sources](../extensibility/source-control-plug-in-api-functions.md)
- [Code de commande](../extensibility/command-code-enumerator.md)
