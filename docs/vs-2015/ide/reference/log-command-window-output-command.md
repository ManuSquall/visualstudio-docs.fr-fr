---
title: Enregistrer la sortie de la fenêtre Commande, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9a5a29cd63f9d51f86d41d2f0f5986a77666318
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666861"
---
# <a name="log-command-window-output-command"></a>Enregistrer la sortie de la fenêtre de commande, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Copie toutes les entrées et sorties de la fenêtre **commande** dans un fichier.

## <a name="syntax"></a>Syntaxe

```
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Arguments
 `filename` Facultatif. Nom du fichier journal. Par défaut, le fichier est créé dans le dossier du profil de l’utilisateur. Si le nom de fichier existe déjà, le journal est ajouté à la fin du fichier existant. Si aucun fichier n’est spécifié, le dernier fichier spécifié est utilisé. Si aucun fichier n’a été spécifié précédemment, le fichier journal cmdline.log est créé par défaut.

> [!TIP]
> Pour modifier l’emplacement d’enregistrement du fichier journal, entrez le chemin complet du fichier, en l’entourant de guillemets s’il comporte des espaces.

## <a name="switches"></a>Commutateurs
 /On facultatif. Démarre le journal pour la fenêtre **Commande** dans le fichier spécifié et ajoute les nouvelles informations à la fin de ce fichier.

 /off facultatif. Arrête le journal pour la fenêtre **Commande**.

 /Overwrite facultatif. Si le fichier spécifié dans l’argument `filename` est identique à un fichier existant, celui-ci est remplacé.

## <a name="remarks"></a>Notes
 Si aucun fichier n’est spécifié, le fichier cmdline.log est créé par défaut. L’alias par défaut de cette commande est Log.

## <a name="examples"></a>Exemples
 Cet exemple crée le fichier journal cmdlog, puis démarre l’enregistrement des commandes.

```
>Tools.LogCommandWindowOutput cmdlog
```

 Cet exemple arrête l’enregistrement des commandes.

```
>Tools.LogCommandWindowOutput /off
```

 Cet exemple reprend l’enregistrement des commandes dans le dernier fichier journal utilisé.

```
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Voir aussi
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [fenêtre commande](../../ide/reference/command-window.md) [Rechercher/zone de commande](../../ide/find-command-box.md) [alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
