---
description: Cette fonction invite l’utilisateur à fournir des options avancées pour une commande donnée.
title: SccGetCommandOptions fonction) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetCommandOptions
helpviewer_keywords:
- SccGetCommandOptions function
ms.assetid: bbe4aa4e-b4b0-403e-b7a0-5dd6eb24e5a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7972d874668649b8bb86adc15008880c5fc4152e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903929"
---
# <a name="sccgetcommandoptions-function"></a>SccGetCommandOptions fonction)
Cette fonction invite l’utilisateur à fournir des options avancées pour une commande donnée.

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
 pvContext

dans Structure de contexte du plug-in de contrôle de code source.

 hWnd

dans Handle de la fenêtre IDE que le plug-in de contrôle de code source peut utiliser comme parent pour toutes les boîtes de dialogue qu’il fournit.

 iCommand

dans Commande pour laquelle des options avancées sont demandées (consultez le [Code de commande](../extensibility/command-code-enumerator.md) pour connaître les valeurs possibles).

 ppvOptions

dans Structure de l’option (peut également être `NULL` ).

## <a name="return-value"></a>Valeur retournée
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :

|Valeur|Description|
|-----------|-----------------|
|SCC_OK|Réussite.|
|SCC_I_ADV_SUPPORT|Le plug-in de contrôle de code source prend en charge les options avancées de la commande.|
|SCC_I_OPERATIONCANCELED|L’utilisateur a annulé la boîte de dialogue **options** du plug-in de contrôle de code source.|
|SCC_E_OPTNOTSUPPORTED|Le plug-in de contrôle de code source ne prend pas en charge cette opération.|
|SCC_E_ISCHECKEDOUT|Impossible d’effectuer cette opération sur un fichier qui est actuellement extrait.|
|SCC_E_ACCESSFAILURE|Un problème est survenu lors de l’accès au système de contrôle de code source, probablement en raison de problèmes de réseau ou de contention. Une nouvelle tentative est recommandée.|
|SCC_E_NONSPECIFICERROR|Échec non spécifique.|

## <a name="remarks"></a>Remarques
 L’IDE appelle cette fonction pour la première fois avec `ppvOptions` = `NULL` pour déterminer si le plug-in de contrôle de code source prend en charge la fonctionnalité options avancées pour la commande spécifiée. Si le plug-in prend en charge la fonctionnalité de cette commande, l’IDE rappelle cette fonction lorsque l’utilisateur demande des options avancées (généralement implémentées comme un bouton **avancé** dans une boîte de dialogue) et fournit un pointeur non null pour `ppvOptions` ce point vers un `NULL` pointeur. Le plug-in stocke toutes les options avancées spécifiées par l’utilisateur dans une structure privée et retourne un pointeur vers cette structure dans `ppvOptions` . Cette structure est ensuite transmise à toutes les autres fonctions d’API de plug-in de contrôle de code source qui doivent en être informées, y compris les appels suivants à la `SccGetCommandOptions` fonction.

 Un exemple peut aider à clarifier cette situation.

 Un utilisateur choisit la commande **obtenir** et l’IDE affiche une boîte de dialogue **obtenir** . L’IDE appelle la `SccGetCommandOptions` fonction avec la `iCommand` valeur `SCC_COMMAND_GET` et la `ppvOptions` valeur `NULL` . Cela est interprété par le plug-in de contrôle de code source comme question « avez-vous des options avancées pour cette commande ? ». Si le plug-in est retourné `SCC_I_ADV_SUPPORT` , l’IDE affiche un bouton **avancé** dans la boîte de dialogue d' **extraction** .

 La première fois que l’utilisateur clique sur le bouton **avancé** , l’IDE appelle à nouveau la `SccGetCommandOptions` fonction, cette fois avec un non- `NULL``ppvOptions` qui pointe vers un `NULL` pointeur. Le plug-in affiche sa propre boîte de dialogue **options d’extraction** , invite l’utilisateur à fournir des informations, place ces informations dans sa propre structure et retourne un pointeur vers cette structure dans `ppvOptions` .

 Si l’utilisateur clique à nouveau sur **avancé** dans la même boîte de dialogue, l’IDE appelle `SccGetCommandOptions` à nouveau la fonction sans modifier `ppvOptions` , afin que la structure soit repassée au plug-in. Cela permet au plug-in de réinitialiser sa boîte de dialogue avec les valeurs précédemment définies par l’utilisateur. Le plug-in modifie la structure en place avant de retourner.

 Enfin, quand l’utilisateur clique sur **OK** dans la boîte de dialogue d' **extraction** de l’IDE, l’IDE appelle [SccGet](../extensibility/sccget-function.md), en transmettant la structure retournée dans `ppvOptions` qui contient les options avancées.

> [!NOTE]
> La commande `SCC_COMMAND_OPTIONS` est utilisée lorsque l’IDE affiche une boîte de dialogue **options** qui permet aux utilisateurs de définir les préférences qui contrôlent le fonctionnement de l’intégration. Si le plug-in de contrôle de code source souhaite fournir sa propre boîte de dialogue de préférences, il peut l’afficher à partir d’un bouton **avancé** dans la boîte de dialogue Préférences de l’IDE. Le plug-in est seul responsable de l’obtention et de la conservation de ces informations. l’IDE ne l’utilise pas ou ne le modifie pas.

## <a name="see-also"></a>Voir aussi
- [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)
- [Code de commande](../extensibility/command-code-enumerator.md)
