---
title: Afficher les modules, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4600f27f62d6e840041a65b4128df128e4d36873
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659533"
---
# <a name="list-modules-command"></a>Afficher les modules, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Répertorie les modules pour le processus en cours.

## <a name="syntax"></a>Syntaxe

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Paramètres
 /Address : `yes|no` facultatif. Spécifie s’il faut afficher les adresses mémoire des modules. La valeur par défaut est `yes`.

 /Name:`yes|no` facultatif. Spécifie s’il faut afficher les noms des modules. La valeur par défaut est `yes`.

 /Order : `yes|no` facultatif. Spécifie s’il faut afficher l’ordre des modules. La valeur par défaut est `no`.

 /Path:`yes|no` facultatif. Spécifie s’il faut afficher les chemins des modules. La valeur par défaut est `yes`.

 /Process : `yes|no` facultatif. Spécifie s’il faut afficher les processus des modules. La valeur par défaut est `no`.

 /SymbolFile : `yes|no` facultatif. Spécifie s’il faut afficher les fichiers de symboles des modules. La valeur par défaut est `no`.

 /SymbolStatus : `yes|no` facultatif. Spécifie s’il faut afficher les états des symboles des modules. La valeur par défaut est `yes`.

 /Timestamp : `yes|no` facultatif. Spécifie s’il faut afficher les horodatages des modules. La valeur par défaut est `no`.

 /Version:`yes|no` facultatif. Spécifie s’il faut afficher les versions des modules. La valeur par défaut est `no`.

## <a name="remarks"></a>Remarques

## <a name="example"></a>Exemples
 Cet exemple répertorie les noms, les adresses et les horodatages des modules pour le processus actuel.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Voir aussi
 [Fenêtre de commande](../../ide/reference/command-window.md) des [commandes Visual Studio](../../ide/reference/visual-studio-commands.md) [Comment : utiliser la fenêtre modules](../../debugger/how-to-use-the-modules-window.md)
