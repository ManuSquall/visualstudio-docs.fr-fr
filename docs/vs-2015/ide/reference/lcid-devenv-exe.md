---
title: -LCID (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: badb88abdf4b3ffd6140cb587b2b0add20630925
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672697"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Définit la langue par défaut utilisée pour le texte, la monnaie et d’autres valeurs au sein de l’environnement de développement intégré (IDE, Integrated Development Environment).

## <a name="syntax"></a>Syntaxe

```
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>Arguments
 `LocaleID` Obligatoire. LCID (ID de paramètres régionaux) de la langue que vous spécifiez.

## <a name="remarks"></a>Remarques
 Charge l’IDE et définit le langage naturel par défaut pour l’environnement. Ce changement est persistant d’une session à une autre et est répercuté dans le volet **Paramètres internationaux** des options **Environnement** de la boîte de dialogue **Options** dans l’IDE.

 Si la langue spécifiée n’est pas disponible sur le système de l’utilisateur, le commutateur /LCID est ignoré.

 Le tableau suivant répertorie les LCID des langues prises en charge par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

|Langue|LCID|
|--------------|----------|
|Chinois (simplifié)|2052|
|Chinois (traditionnel)|1028|
|Anglais|1033|
|Français|1036|
|Allemand|1031|
|Italien|1040|
|Japonais|1041|
|Coréen|1042|
|Espagnol|3082|

## <a name="example"></a>Exemples
 Cet exemple charge l’IDE avec des chaînes de ressources en anglais.

```
devenv /LCID 1033
```

## <a name="see-also"></a>Voir aussi
 [Commutateurs de ligne de commande devenv](../../ide/reference/devenv-command-line-switches.md) [paramètres internationaux, environnement, boîte de dialogue Options personnalisation des dispositions de](../../ide/reference/international-settings-environment-options-dialog-box.md) [fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md)
