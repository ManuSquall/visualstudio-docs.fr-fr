---
title: AddMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41a71a69c916bf2fff30b2dee8784d5d9997436b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705568"
---
# <a name="addmessage"></a>AddMessage
Ajoute un message personnalisé pour les diagnostics graphiques *HUD* (Head-Up Display).

## <a name="syntax"></a>Syntaxe

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Paramètres
 `szMessage` Le message à ajouter à la HUD.

## <a name="remarks"></a>Remarques
 Graphics diagnostics HUD s’affiche dans le coin supérieur gauche de l’application qui s’exécute dans graphics diagnostics. Il affiche des informations d’exécution sur l’application et capture des informations graphiques, ainsi que les messages qui sont ajoutés en appelant cette fonction.

 Pour ajouter un message au HUD, vous n’êtes pas obligé d’être activement capture d’informations graphiques, autrement dit, un message peut être ajouté via une instance de la `VsgDbg` (classe), mais la [Init](init.md) fonction membre n’afin de ne pas être appelée en premier. Les messages sont affichés uniquement dans le HUD, elles ne sont pas enregistrées dans le fichier journal de graphisme.