---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9958e6e9a540dce1a405df8991780600b8f4a702
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665601"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Supprime les commandes et l’interface utilisateur des commandes associées au complément.

## <a name="syntax"></a>Syntaxe

```
Devenv /ResetAddin AddIn
```

## <a name="arguments"></a>Arguments
 `AddIn` Facultatif. Nom de commande du complément.

## <a name="remarks"></a>Remarques
 Par défaut, le nom de commande du complément est égal à *\<nom_solution_complément>* .Connect<em>.\<nom_solution_complément></em> et s’affiche dans Connect.cs en tant que paramètre `commandName` de la méthode `Exec`. Vous pouvez également vérifier le nom de la commande en tapant les premières lettres du nom du complément dans la fenêtre Commandes de Visual Studio, puis en utilisant Intellisense pour compléter la saisie.

## <a name="example"></a>Exemples
 L’exemple suivant démarre Visual Studio et empêche le complément `MyAddin` de s’exécuter au démarrage.

```
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin
```

## <a name="see-also"></a>Voir aussi
 [Personnalisation des paramètres de développement dans](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) les [commutateurs de ligne de commande devenv](../../ide/reference/devenv-command-line-switches.md) de Visual Studio
